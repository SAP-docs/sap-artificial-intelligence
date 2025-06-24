<!-- loio6712bfe6ee5f4b9dadd091c0d8a53fb5 -->

# Create a Resource Group for Grounding



<a name="loio6712bfe6ee5f4b9dadd091c0d8a53fb5__steps_icj_ncy_ycc"/>

## Procedure

Create a resource group by sending a curl request, including the label that makes the resource group available to the grounding service.

> ### Note:  
> Resource group Ids must be of length minimum: 3, maximum: 253. The first and last characters must be either a lowercase letter, an uppercase letter, or a number. Character entries from the second to penultimate can include a lower case letter, an upper case letter, a number, a period \(.\), or a hyphen \(-\). No other special characters are permitted.

```
curl --location --request POST "$AI_API_URL/v2/admin/resourceGroups" 
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--data-raw '{
  "resourceGroupId": "{{resource_group}}",   // Resource group ID to manage document grounding
  "labels": [                                // Labels for specifying resource purpose
    {
      "key": "ext.ai.sap.com/document-grounding",  // Key for Document Grounding feature
      "value": "true"                              // Enable Document Grounding
    }
  ]
}'
```

Existing resource groups can be made available to the grounding service using a `PATCH` request, including the `document-grounding` label.

**Related Information**  


[Edit a Resource Group](edit-a-resource-group-3f88c30.md "")

[Delete a Resource Group](delete-a-resource-group-40d83a2.md "")

