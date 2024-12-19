<!-- loio9d39e7b7afb04d55b1a8cd85b8f18ab9 -->

# Get All Documents in a Collection



## Context

Retrieve details of all documents within a collection. For more information, see [Get Collections](get-collections-0cb4f25.md).



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents`

 > ### Sample Code:  
> ```
> curl --request GET \  # Use GET method to retrieve documents
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents \  # URL to fetch all documents in the collection
>   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> 
> ```

 