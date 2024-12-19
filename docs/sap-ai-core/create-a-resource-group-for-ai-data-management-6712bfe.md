<!-- loio6712bfe6ee5f4b9dadd091c0d8a53fb5 -->

# Create a Resource Group for AI Data Management



<a name="loio6712bfe6ee5f4b9dadd091c0d8a53fb5__context_mqx_wzw_kxb"/>

## Context

> ### Note:  
> Resource group Ids must be of length minimum: 3, maximum: 253. The first and last characters must be either a lowercase letter, an uppercase letter, or a number. Character entries from the second to penultimate, may include a lower case letter, an upper case letter, a number, a period \(.\), or a hyphen \(-\). No other special characters are permitted.



<a name="loio6712bfe6ee5f4b9dadd091c0d8a53fb5__steps_icj_ncy_ycc"/>

## Procedure

Create a resource group by sending a curl request, including the label that makes the resource group available to the grounding service.

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



<a name="loio6712bfe6ee5f4b9dadd091c0d8a53fb5__postreq_q3k_pfk_ddc"/>

## Next Steps

To edit a resource group, see [Edit a Resource Group](https://help.sap.com/docs/AI_CORE/52b4adb30e6744709d6226d2b0659dea/3f88c30813704fd9ba7be3a256afa3c6.html).

To delete a resource group, see [Delete a Resource Group](https://help.sap.com/docs/AI_CORE/52b4adb30e6744709d6226d2b0659dea/40d83a2716894174b4b9b407396a0708.html).

