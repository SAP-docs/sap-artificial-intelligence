<!-- loio991388516a8642b6aa49672937cbc937 -->

# Metadata

You can choose to include metadata in the output structure of the grounding module in orchestration. You can leverage the metadata in your prompt template.



<a name="loio991388516a8642b6aa49672937cbc937__prereq_pqt_5md_32c"/>

## Prerequisites

You have a running orchestration deployment. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).

You have onboarded a repository. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-fbf4dae.md).



## Context

Meta data inclusion is optional, and can be included using the `metadata_params` field in the completions endpoint of the API. The `metadata_params` field takes a list of comma separated strings.



## Procedure

1.  **Optional:** Retrieve supported metadata keys by sending your query to the endpoint `{{AI_API_Url}}/v2/lm/document-grounding/retrieval/search`.

    > ### Sample Code:  
    > ```
    > curl --request POST \
    >   --url {{AI_API_URL}}/v2/lm/document-grounding/retrieval/search \
    >   --header 'AI-Resource-Group: <resource_group>' \
    >   --header 'Authorization: Bearer <access_token>' \
    >   --header 'Content-Type: application/json' \
    >   --data '{
    >   "query": "what is SAP Joule",
    >   "filters": [
    >     {
    >       "id": "string",
    >       "searchConfiguration": {
    >         "maxChunkCount": 5
    >       },
    >       "dataRepositories": [
    >         "*"
    >       ],
    >       "dataRepositoryType": "vector",
    >       "dataRepositoryMetadata": [
    >         {
    >           "key": "type",
    >           "value": [
    >             "custom"
    >           ]
    >         }
    >       ],
    >       "documentMetadata": [],
    >       "chunkMetadata": []
    >     }
    >   ]
    > }'
    > ```

    The response includes details metadata parameters on the following levels: `dataRepository`,`document` and `chunk`.

2.  To include metadata as part of your request, use `metadata_params` and include them as comma separated strings.

    The following example requests that `source` and `webUrl` metadata is included in the results

    > ### Sample Code:  
    > ```
    > curl --request POST \
    >   --url {{AI_API_URL}}/v2/inference/deployments/d3ebb2a32ae870f7/completion \
    >   --header 'Authorization: Bearer <access_token>' \
    >   --header 'ai-resource-group: <resource_group>' \
    >   --header 'content-type: application/json' \
    >   --data '{
    >   "orchestration_config": {
    >     "module_configurations": {
    >       "grounding_module_config": {
    >         "type": "document_grounding_service",
    >         "config": {
    >           "filters": [
    >             {
    >               "id": "filter1",
    >               "data_repositories": [
    >                 "*"
    >               ],
    >               "search_config": {},
    >               "data_repository_type": "vector"
    >             }
    >           ],
    >           "input_params": [
    >             "groundingRequest"
    >           ],
    >           "output_param": "groundingOutput",
    >           "metadata_params": ["source", "webUrl"]
    > 
    >         }
    >       },
    >       "llm_module_config": {
    >         "model_name": "gemini-1.5-pro",
    >         "model_params": {},
    >         "model_version": "001"
    >       },
    >       "templating_module_config": {
    >         "template": [
    >           {
    >             "role": "user",
    >             "content": "You are a helpful assistant for any queries for SAP Teched 2024.\\nAnswer the grounding request by providing relevant answers that fit to the request. \\n\\nRequest: {{ ?groundingRequest }}\\n\\nReports:{{ ?groundingOutput }}"
    >           }
    >         ],
    >         "defaults": {}
    >       },
    >       "filtering_module_config": {
    >         "input": {
    >           "filters": [
    >             {
    >               "type": "azure_content_safety",
    >               "config": {
    >                 "Hate": 2,
    >                 "SelfHarm": 2,
    >                 "Sexual": 2,
    >                 "Violence": 2
    >               }
    >             }
    >           ]
    >         },
    >         "output": {
    >           "filters": [
    >             {
    >               "type": "azure_content_safety",
    >               "config": {
    >                 "Hate": 2,
    >                 "SelfHarm": 2,
    >                 "Sexual": 2,
    >                 "Violence": 2
    >               }
    >             }
    >           ]
    >         }
    >       }
    >     }
    >   },
    >   "input_params": {
    >     "groundingRequest": "what is SAP Joule?"
    >   }
    > }'
    > ```

    > ### Output Code:  
    > ```
    > [
    >  {
    >    "content": "2 FeaturesnJoule is a multitenant software as a service (SaaS) application in SAP Business T echnology Platform. It enablesnthe companion of the Intelligent Enterprise, guiding you through content discovery within SAP Ecosystem,nand giving a transparent role-based access to the relevant processes from everywhere. This is the ONE digitalnassistant experience, a unified  and delightful UX across SAPu2019s solution portfolio.nThe following features are available for Joule:nKey Feature UsenIntegration with SAP application Conversational user interface that is integrated with SAPnapplications. It is a rich web client that renders assistantnresponses using SAP Fiori compliant UI controls.nEnterprise-readiness Out-of-the-box integration with SAP backend systems. Com-npliant with AI ethics, GDPR, privacy controls with SOC-IIncompliance.nPublish and subscribe mechanism Capabilities based on your SAP solution portfolio are bun-ndled into a unique digital assistant.",
    >    "metadata": {
    >      "source": [
    >        "/tmp/document_1.pdf"
    >      ],
    >      "webUrl": [
    >        "https://<sharepoint_url>/sites/<Documents>/sap_joule.pdf"
    >      ],
    >      "document_webUrl": [
    >        "https://<sharepoint_url>/sites/<Documents>/sap_joule.pdf"
    >      ]
    >    }
    >  },
    >  {
    >    "content": "4 Compliance and SecuritynJoule ensures cloud security at multiple levels:nCertificates  and ReportsnJoule regularly undergoes audits and reviews of its policies and controls.nu2022For the complete list of compliance and security standards that the Joule service is compliant with, seenSAP Cloud Platform ISO Certificatesn .nu2022For the complete list of Service Organizational Control (SOC) audit reports available for the Joule service,nsee SAP Cloud Platform SOC Reportsn .nData ProtectionnJoule follows SAP's global data protection and privacy guidelines. For more information on the guidelines, seenData Privacyn .nT o access the Personal Data Processing policy for your region, see Personal Data Processing for SAP CloudnServicesn .n6 PUBLICFeature Scope Description for JoulenCompliance and Security",
    >    "metadata": {
    >      "source": [
    >        "/tmp/document_1.pdf"
    >      ],
    >      "webUrl": [
    >        "https://<sharepoint_url>/sites/<Documents>/sap_joule.pdf"
    >      ],
    >      "document_webUrl": [
    >        "https://<sharepoint_url>/sites/<Documents>/sap_joule.pdf"
    >      ]
    >    }
    >  }
    > ```

3.  Leverage the metadata in your prompt

    Include instructions in your prompt for how the model should use the metadata.

    > ### Sample Code:  
    > ```
    > "templating_module_config": {
    >   "template": [
    >       {
    >       "role": "user",
    >       "content": "You are a helpful assistant for any queries for SAP Teched 2024.\\nAnswer the grounding request by providing relevant answers that fit to the request. \\n\\nRequest: {{ ?groundingRequest }}\\n\\nReports:{{ ?groundingOutput }} Alongwith the original response, provide another response by making use of metadata received in the grounding output to provide more optimal response. Explain how the metadata was used."
    >    }
    >   ],
    >    "defaults": {}
    > }
    > ```

    > ### Note:  
    > If a metadata name is present on multiple levels, the result will include a `parent_KeyName` naming convention. The following example shows that `webUrl` is present on the chunk and document levels:
    > 
    > > ### Output Code:  
    > > ```
    > > "metadata": {
    > >   "webUrl": "<value from chunk metadata>",
    > >   "document_webUrl": "<value from document metadata>"
    > > }
    > > ```


