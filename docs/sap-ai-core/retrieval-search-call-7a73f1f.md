<!-- loio7a73f1f525404759bb99296b63eca609 -->

# Retrieval Search call

The retrieval search call searches data repositories and returns the relevant chunks for the user query.



<a name="loio7a73f1f525404759bb99296b63eca609__prereq_xqg_l2h_jdc"/>

## Prerequisites

You have created a resource group for grounding purposes. For more information, see [Create a Resource Group for AI Data Management](create-a-resource-group-for-ai-data-management-6712bfe.md)

You have created a generic secret for grounding purposes. For more information, see [Create a Generic Secret for AI Data Management](create-a-generic-secret-for-ai-data-management-bdea357.md)



<a name="loio7a73f1f525404759bb99296b63eca609__context_e42_ngh_jdc"/>

## Context

The following repository types are supported:

-   vector




<a name="loio7a73f1f525404759bb99296b63eca609__steps_uyc_chh_jdc"/>

## Procedure

Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/retrieval/search`

To search within a specific repository specify it's `repositoryid` in `dataRepositories` attribute of the request or specify `*` to search in all the repositories.

For example:

> ### Sample Code:  
> ```
> 
> curl --request POST \  # Use POST method to initiate the search query in the retrieval API
>   --url $AI_API_URL/v2/lm/document-grounding/retrieval/search \  # Specify the endpoint URL to trigger the search in data repositories
>   --header 'AI-Resource-Group: {{resource_group}}' \  # Add the resource group ID in the header to specify the resource group for the query
>   --data '{
>   "query": "<user query to look for an answer in vector database>",  # User query that will be used to search the data repository
>   "filters": [  # Optional filters to customize the search, such as the repository and metadata constraints
>     {
>       "id": "string",  # Identifier for the filter, can be a custom string to track or categorize the filter
>       "searchConfiguration": {
>         "maxChunkCount": 1  # Limit the number of chunks returned in the search results (e.g., 1 chunk)
>       },
>       "dataRepositories": [
>         "<data repository id or '*' >"  # Specify a specific repository ID or use '*' to search across all repositories
>       ],
>       "dataRepositoryType": "vector",  # The type of repository to search in, can be either "vector"
>       "dataRepositoryMetadata": [  # Optional metadata filters for data repositories to refine the search
>         {  # Example metadata filter for data repository
>           "key": "type",  # The metadata key to filter on
>           "value": [
>             "custom"  # Metadata value for the key (can filter by specific repository types, e.g., "custom")
>           ]
>         }
>       ],
>       "documentMetadata": [  # Optional metadata filters for the documents within the repository
>         {  # Example document metadata filter
>           "key": "url",  # The metadata key for document (e.g., filtering based on document URL)
>           "value": [
>             "http://hello.com",  # The value to match (e.g., URL of the document)
>             "123"  # Another value for URL filter or other document identifiers
>           ]
>         }
>       ],
>       "chunkMetadata": [  # Optional metadata filters for chunk-level metadata
>         {  # Example chunk metadata filter
>           "key": "index",  # The metadata key for chunk (e.g., filtering based on chunk index)
>           "value": [
>             "1"  # The value to match (e.g., retrieve chunk with index 1)
>           ]
>         }
>       ]
>     }
>   ]
> }'
> 
> ```

