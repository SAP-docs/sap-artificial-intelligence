<!-- loiocbebcf6a1ea846a881fea993966ae8db -->

# Delete Documents



## Procedure

Send a DELETE request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents/{{documentId}}`

 > ### Sample Code:  
> ```
> 
> curl --request DELETE \  # Use DELETE method to remove the document
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents/{{documentId}} \  # URL with collection ID and document ID
>   --header 'AI-Resource-Group: {{resource_group}}'  # Specify the resource group ID
> 
> ```

 