<!-- loio8bd58cb0fc4f4269870964fb586995f9 -->

# Grant SAP AI Core Access to Data Products

Adjust the integration process so that SAP AI Core can access data products through embedded SAP Business Data Cloud Connect using a delegation mechanism. This process involves extending SPII callback implementations and configuring data destinations, tabular artifacts, and scenario configurations across Wave 0 and Wave 2 phases.



## Context

Integrating embedded SAP Business Data Cloud Connect with SAP AI Core follows the delegation mechanism, whereby your line of business \(LoB\) declares SAP AI Core as a delegate in its Wave 0 SPII response. The embedded SAP Business Data Cloud Connect subsequently creates the relevant authorization policies on behalf of SAP AI Core.

This process requires you to extend both the Wave 0 and Wave 2 SPII callback implementations in your LoB application. You must also add the calls to the Context Registry API in SAP AI Core.



## Procedure

**Wave 0:**

1.  Register SAP AI Core as a delegate.

    When you onboard the tenant \(initiated by Wave 0 of the SPII contract\), the LoB must complete the following steps:

    1.  Create a data destination in SAP AI Core for the customer's resource group.

        Call the Context Registry API in SAP AI Core to create a data destination in the customer's resource group. As the host, you can set a placeholder at this point. The host is updated in Wave 2 when the actual endpoint in SAP BDC Connect is known.

        ```
        curl -X PUT "$AI_API_URL/v2/tcr/dataDestinations/bdc-connect-<tenant-id>" \
          -H "Authorization: Bearer $TOKEN" \
          -H "AI-Resource-Group: $RESOURCE_GROUP_ID" \
          -H "Content-Type: application/json" \
          -d '{
            "description": "SAP BDC Connect delta sharing endpoint for tenant <tenant-id>",
            "type": "DELTA_SHARING",
            "adapterType": "DeltaShare",
            "config": {
              "host": "placeholder"
            }
          }'
        
        ```

        The response includes the `subjectPatterns` property. The values of this property are the mutual Transport Layer Security \(mTLS\) certificate subjects that SAP AI Core presents when it accesses the data. Two subject patterns are typically used: one for SAP AI Core's own PKI certificate and one for the internal SAP HANA instance:

        ```
        {
          "name": "bdc-connect-<tenant-id>",
          "subjectPatterns": [
            "<ai-core-cert-subject-pattern>",
            "<ai-core-hana-cert-subject-pattern>"
          ]
        }
        
        ```

        > ### Note:  
        > You can identify the SAP HANA certificate by the `CN=HANA_` prefix in the subject pattern. The certificate for SAP AI Core uses a hex-encoded certificate number without a prefix.

    2.  Declare SAP AI Core and SAP HANA as `applicationDelegates` in the Wave 0 SPII response.

        Include both `subjectPatterns` from the data destination response as delegates in the Wave 0 SPII callback. That is, include SAP AI Core's own certificate as `SAPCloudX509` and the SAP HANA certificate as `HANA`:

        ```
        {
          "credentials": {
            "outboundCommunication": {
              "clientCertificateAuthentication": {
                "applicationDelegates": [
                  {
                    "type": "SAPCloudX509",
                    "delegate": {
                      "certificate": "<ai-core-cert-subject-pattern>"
                    }
                  },
                  {
                    "type": "HANA",
                    "delegate": {
                      "certificate": "<ai-core-hana-cert-subject-pattern>"
                    }
                  }
                ]
              }
            }
          }
        }
        ```

        The embedded SAP BDC Connect receives this response, stores the delegate request, and injects its own certificate for the producer of the data product. In Wave 1, the producer registers the certificate and returns the HDLFS connection properties. In Wave 2, SAP BDC Connect replaces the producer's connection properties with its own HDLFS endpoint and creates authorization policies for the certificate subject declared by SAP AI Core.



**Wave 2:**

2.  Update the data destination and create tabular artifacts.

    When the LoB application receives the Wave 2 SPII callback, the embedded SAP BDC Connect provides the final connection configuration. This configuration includes the actual HDLFS endpoint URL and the delta sharing share name for each granted data product. The schema and table names within a share are use-case-specific: they depend on which tables of the data product are needed for inference, and are known to the LoB implementation.

    The LoB must complete the following steps:

    1.  Update the data destination with the actual HDLFS endpoint.

        Extract the HDLFS files from the Wave 2 configuration and update the data destination created in Wave 0:

        ```
        curl -X PUT "$AI_API_URL/v2/tcr/dataDestinations/bdc-connect-<tenant-id>" \
          -H "Authorization: Bearer $TOKEN" \
          -H "AI-Resource-Group: $RESOURCE_GROUP_ID" \
          -H "Content-Type: application/json" \
          -d '{
            "description": "BDC Connect delta sharing endpoint for tenant <tenant-id>",
            "type": "DELTA_SHARING",
            "adapterType": "DeltaShare",
            "config": {
              "host": "<bdc-connect-sharing-host-from-wave2>"
            }
          }'
        ```

    2.  Create a tabular artifact for each data product table.

        For each table that your LoB wants SAP AI Core to access, create a tabular artifact that references the data destination. Use the delta sharing share name from the Wave 2 configuration. The schema and table names are specific to each use case and known to the LoB.

        ```
        curl -X PUT "$AI_API_URL/v2/tcr/tabularArtifacts/<artifact-name>" \
          -H "Authorization: Bearer $TOKEN" \
          -H "AI-Resource-Group: $RESOURCE_GROUP_ID" \
          -H "Content-Type: application/json" \
          -d '{
            "dataDestinationName": "bdc-connect-<tenant-id>",
            "type": "DELTA",
            "path": "/<share_name>/<schema_name>/<table_name>",
            "csnMetadata": {
              "definition": {
                "definitionType": "AUTO"
              }
            }
          }'
        ```

    3.  Create a scenario configuration.

        Group the tabular artifacts for a predictive scenario under a named scenario configuration.

        ```
        curl -X PUT "$AI_API_URL/v2/tcr/scenarioConfigurations/<scenario-name>" \
          -H "Authorization: Bearer $TOKEN" \
          -H "AI-Resource-Group: $RESOURCE_GROUP_ID" \
          -H "Content-Type: application/json" \
          -d '{
            "tabularArtifacts": [
              {
                "name": "<artifact-name>"
              }
            ]
          }'
        ```





## Results

SAP AI Core can now use the scenario configuration at inference time to retrieve context rows from the SAP BDC Connect data product.



### Inference Call

The LoB application invokes the `tabular-orchestration` virtual deployment, which is a system-level deployment in SAP AI Core that doesn't require a custom deployment. The inference request references the scenario configuration by name and passes the prediction query features. SAP AI Core's tabular orchestration layer fetches the relevant context rows from the embedded SAP BDC Connect via the data destination, and then forwards the query together with the context to the tabular foundation model \(such as `SAP-RPT-1`\).

