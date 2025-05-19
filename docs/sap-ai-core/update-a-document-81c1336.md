<!-- loio81c1336742bd4dd3b581e04cb6a8f7ca -->

# Update a Document



## Procedure

Send a PATCH request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents`

 > ### Sample Code:  
> ```
> 
> curl --request PATCH \  # Use PATCH method to update a document
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents \  # Endpoint to update a document in a collection
>   --header 'AI-Resource-Group: {{resource_group}}' \  # Include the resource group ID in the header
>   --header 'Content-Type: application/json' \
>   --data '{
>   "documents": [
>     {
>       "id": {{documentId}},  // Document ID of the document to be updated
>       "metadata": [  // Metadata to update
>         {
>           "key": "url",
>           "value": [
>             "http://hello.com",
>             "123"
>           ]
>         }
>       ],
>       "chunks": [  // Array of document chunks
>         {
>           "content": "<This is an updated document chunk content>",  // Updated content for chunk 1
>           "metadata": [  // Updated metadata for chunk 1
>             {
>               "key": "index",
>               "value": [
>                 "1"
>               ]
>             }
>           ]
>         },
>         {
>           "content": "<No update to chunk 2>",  // Content for chunk 2 remains unchanged
>           "metadata": [  // Metadata for chunk 2 remains unchanged
>             {
>               "key": "index",
>               "value": [
>                 "2"
>               ]
>             }
>           ]
>         }
>       ]
>     }
>   ]
> }'
> ```

 