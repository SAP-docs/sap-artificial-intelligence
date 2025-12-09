<!-- loioe32efa5402154101b4cc05c03ef5be09 -->

# Create a Resource Group for Grounding



<a name="loioe32efa5402154101b4cc05c03ef5be09__section_vcf_xqs_dgc"/>

## Prerequisites

Resource groups represent a virtual collection of related resources within the scope of one tenant. When a tenant is onboarded, the system immediately creates a default resource group. Tenant administrators can create or delete additional resource groups using the AI API. Tenants can map resource groups based on corresponding usage scenarios.

If a tenant uses resource groups to isolate scenario consumer tenants and those resource groups are deleted, the scenario consumers are deprovisioned. The service does not recognize the scenario consumer of the tenant. The standard XUSAA multitenancy model is followed.

For more information, see [Scope of Resources](scope-of-resources-c9518c0.md).



## Procedure

1.  Create a resource group by sending a curl request, including the label that makes the resource group available to the grounding service.

    > ### Note:  
    > Resource group Ids must be of length minimum: 3, maximum: 253. The first and last characters must be either a lowercase letter, an uppercase letter, or a number. Character entries from the second to penultimate can include a lower case letter, an upper case letter, a number, a period \(.\), or a hyphen \(-\). No other special characters are permitted.

    Set the following in the headers:

    -   `AI_API_URL`: the base URL of your SAP AI Core environment.
    -   `{{resource_group}}`: The AI resource group ID or document grounding management
    -   `{{access_token}}`: Your access token for SAP AI Core

    ```
    curl --location --request POST "$AI_API_URL/v2/admin/resourceGroups" 
    --header "Authorization: Bearer {{access_token}}" \
    --header 'Content-Type: application/json' \
    --data-raw '{
      "AI-Resource-Group": "{{resource_group}}", 
      "labels": [
        {
          "key": "ext.ai.sap.com/document-grounding",
          "value": "true"
        }
      ]
    }'
    ```

    Existing resource groups can be made available to the grounding service using a `PATCH` request, including the `document-grounding` label.




<a name="loioe32efa5402154101b4cc05c03ef5be09__section_mpf_c5y_fgc"/>

## Next Steps

To provide data chunks for ingestion without registering a repository, use the Vector API data management API. For more information, see [Vector API](vector-api-08e3d00.md).

To register a repository to use as part of a grounding pipeline, create a generic secret for grounding for the repository of your choice. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).

**Related Information**  


[Edit a Resource Group](edit-a-resource-group-3f88c30.md "")

[Delete a Resource Group](delete-a-resource-group-40d83a2.md "")

