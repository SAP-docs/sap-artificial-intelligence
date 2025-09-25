<!-- copy4af7e1f7b522443584cc73876aad38c8 -->

# Data Pipelines

You can get the details of your data pipelines using the following endpoints:



<a name="copy4af7e1f7b522443584cc73876aad38c8__section_tp4_cnb_4fc"/>

## Get All Pipelines

Use this endpoint to retrieve all document grounding pipelines created in your specified AI resource group.

Each pipeline represents a configured end-to-end process that:

-   Fetches documents from a supported data source

-   Preprocesses and chunks the content

-   Stores semantic embeddings into the HANA Vector Store


This is useful when you want to:

-   Review existing pipelines before creating or executing a new one

-   Manage pipeline inventory programmatically

-   Support dashboards, monitoring, or integration flows

-   Enable pipeline reusability across projects


> ### Note:  
> If you use the Pipeline APIs for creating and retrieving Pipeline details, you do not need to use the Vector API separately, it’s already handled as part of the pipeline execution. After a pipeline runs, you can use the Retrieval API to query grounded content.
> 
> The endpoint for retrieving document pipelines is `$AI_API_URL/v2/lm/document-grounding/pipelines`

You can use the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines` to retrieve all document grounding pipelines.

Populate the code snippet with the following:

-   `{{resource_group}}`: the AI resource group ID assigned to your account.

-   `AI_API_URL`: the base URL of your SAP AI Core environment.

-   `{{access_token}}`: Your access token for SAP AI Core

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines\
>   --header 'AI-Resource-Group: {{resource_group}}' \ 
>   --header 'Authorization: Bearer {{access_token}}'
> ```

This endpoint returns a response containing an array of pipeline objects, in JSON format.

The available statuses for pipelines are the following:

-   NEW
-   UNKNOWN
-   INPROGRESS
-   FINISHED
-   FINISHEDWITHERRORS
-   TIMEOUT



### Pagination Support

You can use OData-compliant query parameters to manage large result sets:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

$top

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Limits the number of results returned. for example., $top=10 returns 10 results.

</td>
</tr>
<tr>
<td valign="top">

$skip

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Skips a specific number of results. for example, $skip=20 skips the first 20.

</td>
</tr>
<tr>
<td valign="top">

$count

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

If true, includes the total count in the response. If false, includes the total number of records in the response.

</td>
</tr>
</table>

For example:

```
curl --request GET  
  --url "$AI_API_URL/v2/lm/document-grounding/pipelines?$top=10&$skip=20&$count=true"  
  --header "AI-Resource-Group: {{resource_group}}"
  --header 'Authorization: Bearer {{access_token}}' 
```



<a name="copy4af7e1f7b522443584cc73876aad38c8__section_wkm_2qb_4fc"/>

## Get Pipeline Details

This endpoint lets you fetch full details of a specific document grounding pipeline by using its unique pipelineId.

It is useful when you want to:

-   Inspect the pipeline’s configuration \(fore example, data source, chunking strategy, schedule\)

-   Debug or validate how a pipeline is set up

-   Display pipeline metadata

-   Get last updated time and status before reusing or modifying a pipeline


You can get pipeline details using the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}`.

Populate the code snippet with the following:

-   `{{resource_group}}`: the ID of the specific pipeline you want to retrieve.

-   `AI_API_URL`: the base URL of your SAP AI Core environment.

-   `{{access_token}}`: Your access token for SAP AI Core
-   `{{pipelineId}}`: the AI resource group ID assigned to your account.


> ### Sample Code:  
> ```
> 
> curl --request GET \ 
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}} \  
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Authorization: Bearer {{access_token}}'
> ```

This endpoint returns a response containing details of the pipeline configuration and metadata, in JSON format.

The available statuses for pipelines are the following:

-   NEW
-   UNKNOWN
-   INPROGRESS
-   FINISHED
-   FINISHEDWITHERRORS
-   TIMEOUT



<a name="copy4af7e1f7b522443584cc73876aad38c8__section_ovl_shh_4fc"/>

## Get Pipeline Status

This endpoint allows you to retrieve the current status of a specific document grounding pipeline. It provides information on the lifecycle state, readiness, or any ongoing processing of the pipeline.

Populate the code snippet with the following:

-   `{{resource_group}}`: the ID of the specific pipeline you want to retrieve..

-   `AI_API_URL`: the base URL of your SAP AI Core environment.

-   `{{access_token}}`: Your access token for SAP AI Core
-   `{{pipelineId}}`: the AI resource group ID assigned to your account.


> ### Sample Code:  
> ```
> 
> curl --request GET \ 
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/status \
>   --header 'AI-Resource-Group: {{resource_group}}' \ 
>   --header 'Authorization: Bearer {{access_token}}'
> 
> 
> ```

This endpoint returns a response containing details of the pipeline status, in JSON format.

The available statuses for pipelines are the following:

-   NEW
-   UNKNOWN
-   INPROGRESS
-   FINISHED
-   FINISHEDWITHERRORS
-   TIMEOUT



<a name="copy4af7e1f7b522443584cc73876aad38c8__section_xxx_snb_4fc"/>

## Delete a Pipeline

Use this endpoint to permanently delete a specific document grounding pipeline by its unique pipelineId. This is typically done when a pipeline is no longer required, misconfigured, or needs to be recreated with different settings. After deletion, the pipeline and its configuration are irreversibly removed.

You can delete a pipeline using the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}`.

Populate the code snippet with the following:

-   `{{resource_group}}`: the ID of the specific pipeline you want to retrieve..

-   `AI_API_URL`: the base URL of your SAP AI Core environment.

-   `{{access_token}}`: Your access token for SAP AI Core
-   `{{pipelineId}}`: the AI resource group ID assigned to your account.


> ### Sample Code:  
> ```
> curl --request DELETE \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}} \
>   --header 'AI-Resource-Group: {{resource_group}}' \ 
>   --header 'Authorization: Bearer {{access_token}}'
> ```

This endpoint returns a response containing confirmation of deletion, in JSON format.

