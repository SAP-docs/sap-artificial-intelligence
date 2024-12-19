<!-- loioa64179d1b8684a519d39dda0afa11e38 -->

# Get a Repository



<a name="loioa64179d1b8684a519d39dda0afa11e38__prereq_xqg_l2h_jdc"/>

## Prerequisites

You have created a resource group for grounding purposes. For more information, see [Create a Resource Group for AI Data Management](create-a-resource-group-for-ai-data-management-6712bfe.md)

You have created a generic secret for grounding purposes. For more information, see [Create a Generic Secret for AI Data Management](create-a-generic-secret-for-ai-data-management-bdea357.md)



<a name="loioa64179d1b8684a519d39dda0afa11e38__context_e42_ngh_jdc"/>

## Context



<a name="loioa64179d1b8684a519d39dda0afa11e38__steps_uyc_chh_jdc"/>

## Procedure

Send a GET request to the endpoint `$AI_API_URL/v2/lm/document-grounding/retrieval/dataRepositories`

To search within a specific repository specify it's `repositoryid` in `dataRepositories` attribute of the request or specify `*` to search in all the repositories.

Example for all repositories:

> ### Sample Code:  
> ```
> curl --request GET \  # Use GET method to retrieve all data repositories
>   --url $AI_API_URL/v2/lm/document-grounding/retrieval/dataRepositories \  # Endpoint to retrieve all data repositories
>   --header 'AI-Resource-Group: {{resource_group}}'  # Add resource group ID in the header for context
> ```

Example for a repository by ID:

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API_URL/v2/lm/document-grounding/retrieval/dataRepositories/{{repositoryId}} \
>   --header 'AI-Resource-Group: {{resource_group}}'  # Replace with your actual resource group ID
> 
> ```



<a name="loioa64179d1b8684a519d39dda0afa11e38__result_ol2_cfr_kdc"/>

## Results

> ### Output Code:  
> ```
> {
>   "resources": [
>     {
>       "id": "<respositoryid>",
>       "title": "<repository title>",
>       "metadata": [ // repository metadata 
>         {
>           "key": "pipeline",
>           "value": [
>             "137f3100-9171-48fb-b8d4-f93804bf7bac"
>           ]
>         },
>         {
>           "key": "type",
>           "value": [
>             "custom"
>           ]
>         },
>         {
>           "key": "pipelineType",
>           "value": [
>             "MSSharePoint"
>           ]
>         }
>       ],
>       "type": "vector"
>     },
>     {
>       "id": "<respositoryid>",
>       "title": "<repository title>",
>       "metadata": [
>         {
>           "key": "purpose",
>           "value": [
>             "demonstration"
>           ]
>         },
>         {
>           "key": "a-random-key",
>           "value": [
>             "hello world!"
>           ]
>         }
>       ],
>     }
>   ],
>   "count": 2
> }
> ```

