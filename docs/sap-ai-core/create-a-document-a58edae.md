<!-- loioa58edaec454d498a88ba5b523485552f -->

# Create a Document



## Context

Add a document with associated metadata and chunks to a collection. For more information, see [Get Collections](get-collections-0cb4f25.md).



## Procedure

Send a POST request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents`

 > ### Sample Code:  
> ```
> 
> curl --request POST \  # Use POST method to create a document
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents \  # Endpoint to add a document to a collection
>   --header 'AI-Resource-Group: {{resource_group}}' \  # Include the resource group ID in the header
>   --header 'Content-Type: application/json' \
>   --data '{
>   "documents": [
>     {
>       "metadata": [  // Metadata for the document
>         {
>           "key": "url",
>           "value": [
>             "http://hello.com",
>             "123"
>           ]
>         }
>       ],
>       "chunks": [  // Content chunks within the document
>         {
>           "content": "<chunk content 1>",  // Text content of chunk 1
>           "metadata": [  // Metadata for chunk 1
>             {
>               "key": "index",
>               "value": [
>                 "1"
>               ]
>             }
>           ]
>         },
>         {
>           "content": "<chunk content 2>",  // Text content of chunk 2
>           "metadata": [  // Metadata for chunk 2
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

 