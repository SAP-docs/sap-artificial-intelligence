<!-- loio4748a3fb2ff245dca3250f09048386b4 -->

# Get Collection Creation Status



## Context

This API call checks the current status of a collection creation process using the collection ID. For more information, see [Get Collections](get-collections-0cb4f25.md).



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{id}}/creationStatus`

 > ### Sample Code:  
> ```
> 
> curl --request GET \  # Use GET method to check collection creation status
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{id}}/creationStatus \  # Endpoint to get the status of collection creation
>   --header 'AI-Resource-Group: {{resource_group}}'  # Include the resource group ID in the header
> 
> ```

 