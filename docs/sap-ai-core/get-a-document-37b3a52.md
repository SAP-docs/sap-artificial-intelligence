<!-- loio37b3a5233e7e4a31b65c8439f3da6ebf -->

# Get A Document



## Context

Retrieve details of a document within a collection. For more information, see [Get Collections](get-collections-0cb4f25.md) and [Get All Documents in a Collection](get-all-documents-in-a-collection-9d39e7b.md).



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents/{{documentId}}`

 > ### Sample Code:  
> ```
> 
> curl --request GET \  # Use GET method to retrieve a specific document
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents/{{documentId}} \  # URL to fetch a specific document
>   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> ```

 