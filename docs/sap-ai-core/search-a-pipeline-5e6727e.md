<!-- loio5e6727e292344d8a98239d1a7d6f64a8 -->

# Search a Pipeline



## Prerequisites

You've created a document grounding pipeline, and included your choice of metadata in the `dataRepositoryMetadata` field. For more information, see [Create a Document Grounding Pipeline Using the Pipelines API \(with Metadata\)](create-a-document-grounding-pipeline-using-the-pipelines-api-with-metadata-3c56d6c.md).



## Procedure

Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/search`. Include your data repository key:value pair in your request.

Set the following in the headers:

-   `AI_API_URL`: the base URL of your SAP AI Core environment.
-   `{{resource_group}}`: The AI resource group ID or document grounding management
-   `{{access_token}}`: Your access token for SAP AI Core

For example:

```
curl --request POST \
--url $AI_API_URL/v2/lm/document-grounding/pipelines/search \
--header 'AI-Resource-Group: {{resource_group}}'
--data '{
    "dataRepositoryMetadata": [
        {
            "key": "example",
            "value": [
                "demo"
            ]
        }
    ]
}'
```

The output lists any pipelines that match the data repository metadata.

> ### Output Code:  
> ```
> {
>     "count": 1,
>     "resources": [
>         {
>             "id": "<pipelineid>",
>             "status": "<status-of-pipeline-execution>",
>             "type": "<type-of-repository>",
>             "configuration": {
>                 "sharePoint": {
>                     "id": "<site-id>",
>                     "name": "<site-name>"
>                 }
>             }
>         }
>     ]
> }
> ```

