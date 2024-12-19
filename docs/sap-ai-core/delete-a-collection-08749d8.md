<!-- loio08749d8194fb45b8bce20b041253f694 -->

# Delete a Collection



## Procedure

Send a DELETE request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}`

 > ### Sample Code:  
> ```
> 
> curl --request DELETE \  # Use DELETE method to remove the collection
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}} \  # URL with the collection ID
>   --header 'AI-Resource-Group: {{resource_group}}'  # Specify the resource group ID
> 
> ```

 