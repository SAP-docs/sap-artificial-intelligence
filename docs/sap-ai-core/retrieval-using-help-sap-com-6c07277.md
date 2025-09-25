<!-- loio6c07277357204ac18e1cf32e2a27107f -->

# Retrieval Using help.sap.com





<a name="loio6c07277357204ac18e1cf32e2a27107f__prereq_pqt_5md_32c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).

You have onboarded a repository. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).



## Context

Meta data inclusion is optional, and can be included using the `metadata_params` field in the completions endpoint of the API. The `metadata_params` field takes a list of comma separated strings.



## Procedure

1.  **Optional:** Retrieve supported metadata keys by sending your query to the endpoint `{{AI_API_Url}}/v2/lm/document-grounding/retrieval/search`.

    > ### Sample Code:  
    > ```
    > curl --request POST \
    >   --url {{AI_API_URL}}/v2/lm/document-grounding/retrieval/search \  
    >   --header 'AI-Resource-Group: <resource_group>' \   
    >   --header 'Authorization: Bearer <access_token>' \
    >   --header 'Content-Type: application/json' \
    >   --data '{
    >   "query": "what is SAP Joule",
    >   "filters": [
    >     {
    >       "id": "string",
    >       "searchConfiguration": {},
    >       "dataRepositories": []
    >         }
    >       ],
    >       "documentMetadata": [],
    >       "chunkMetadata": []
    >     }
    >   ]
    > }'
    > ```

    The response includes details of metadata parameters on the following levels: `dataRepository`,`document` and `chunk`.

2.  To include metadata as part of your request, use `metadata_params` and include them as comma separated strings.

    The following example requests that `source` and `webUrl` metadata is included in the results

    > ### Sample Code:  
    > ```
    > curl --request POST \
    >   --url {{ORCH_DEPLOYMENT_URL}}/v2/completion \  
    >   --header 'Authorization: Bearer <access_token>' \  
    >   --header 'AI-Resource-Group: <resource_group>' \
    >   --header 'content-type: application/json' \
    >   --data '{
    >     "config": {
    >         "modules": {
    >             "grounding": {
    >                 "type": "document_grounding_service",
    >                 "config": {
    >                     "filters": [
    >                         {
    >                             "id": "filter1",
    >                             "data_repositories": [
    >                                 "*"
    >                             ],
    >                             "search_config": {},
    >                             "data_repository_type": "help.sap.com",
    >                             "document_metadata": []
    >                         }
    >                     ]
    >                 }
    >             }
    >         },
    >         "placeholders": {
    >             "input": [
    >                 "groundingRequest"
    >             ],
    >             "output": "groundingOutput",
    >             "prompt_templating": {
    >                 "prompt": {
    >                     "template": [
    >                         {
    >                             "role": "user",
    >                             "content": "<prompt>: {{?groundingRequest}}\n\nReports: {{?groundingOutput}}"
    >                         }
    >                     ]
    >                 },
    >                 "model": {
    >                     "name": "<modelName>",
    >                     "version": "<modelVersion>",
    >                     "params": {
    >                         "max_tokens": 50,
    >                         "temperature": 0.1,
    >                         "frequency_penalty": 0,
    >                         "presence_penalty": 0
    >                     }
    >                 }
    >             }
    >         }
    >     },
    >     "placeholder_values": {
    >         "groundingRequest": "<grounding request>"
    >     }
    > }'
    > ```


