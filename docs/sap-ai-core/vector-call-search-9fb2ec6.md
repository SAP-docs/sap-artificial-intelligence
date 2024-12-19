<!-- loio9fb2ec64f6a847e49bbe4f8d7106f7f6 -->

# Vector Call Search



## Context

Search for relevant chunks in a collection or across all collections based on a user query. The response contains chunks that match the query, filtered by collection and document metadata.



## Procedure

Send a: POST request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/search`

 > ### Sample Code:  
> ```
> curl --request POST \  # Use POST method to perform search
>   --url $AI_API_URL/v2/lm/document-grounding/vector/search \  # URL for vector search
>   --header 'AI-Resource-Group: {{resource_group}}' \  # Specify resource group ID
>   --header 'Content-Type: application/json' \  # Define content type as JSON
>   --data '{
>   "query": "is Joule an AI Copilot?", 
>   "filters": [
>     {
>       "id": "String",
>       "collectionIds": [
>         "*" OR collection_id # Search across all collections OR Specify specific collection ID
>       ],
>       "configuration": {},
>       "collectionMetadata": [],
>       "documentMetadata": [
>         {
>           "key": "url",
>           "value": [
>             "http://hello.com",
>             "1234"
>           ]
>         }
>       ],
>       "chunkMetadata": []
>     }
>   ]
> }'
> ```

 