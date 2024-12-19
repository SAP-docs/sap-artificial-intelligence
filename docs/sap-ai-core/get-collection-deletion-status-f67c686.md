<!-- loiof67c6861a26d4de7a0e23dc75ec8515d -->

# Get Collection Deletion Status



## Context

Check the current status of a collection deletion. For more information, see [Get Collections](get-collections-0cb4f25.md).



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{id}}/deletionStatus`

 > ### Sample Code:  
> ```
> 
> curl --request GET \  # Use GET method to check deletion status
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{id}}/deletionStatus \  # URL with collection ID for status check
>   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> 
> 
> ```

 