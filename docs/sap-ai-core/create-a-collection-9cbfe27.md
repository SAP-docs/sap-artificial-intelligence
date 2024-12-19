<!-- loio9cbfe270add641c291bb516d8afe3ce9 -->

# Create a Collection



<a name="loio9cbfe270add641c291bb516d8afe3ce9__prereq_tzh_5tr_kdc"/>

## Prerequisites

You have created a resource group for grounding purposes. For more information, see [Create a Resource Group for AI Data Management](create-a-resource-group-for-ai-data-management-6712bfe.md)

You have created a generic secret for grounding purposes. For more information, see [Create a Generic Secret for AI Data Management](create-a-generic-secret-for-ai-data-management-bdea357.md)



<a name="loio9cbfe270add641c291bb516d8afe3ce9__context_ov1_1wr_kdc"/>

## Context

You can add a new document collection in the SAP HANA Vector Database for document grounding in generative AI hub.



<a name="loio9cbfe270add641c291bb516d8afe3ce9__steps_wgp_c5r_kdc"/>

## Procedure

Send a POST request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections`

 > ### Sample Code:  
> ```
> 
> curl --request POST \  # Use POST method to create a collection
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections \  # Endpoint to create a new collection
>   --header 'AI-Resource-Group: {{resource_group}}' \  # Resource group ID for targeting the collection's location
>   --data '{
>   "title": "<title of the collection>",  // Define collection title
>   "embeddingConfig": {
>     "modelName": "<embedding-model-name>"
>   },
>   "metadata": [
>     {
>       "key": "purpose",
>       "value": [
>         "<text>"  // Purpose of this collection
>       ]
>     },
>     {
>       "key": "<a-random-key>",
>       "value": [
>         "<text>"  // Example metadata value
>       ]
>     }
>   ]
> }'
> ```

 