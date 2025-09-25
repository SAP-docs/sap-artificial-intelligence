<!-- copy174102376a3e4032ba82bd81889d41e2 -->

# Documents

You can get the details of your documents in data pipelines using the following endpoints:



<a name="copy174102376a3e4032ba82bd81889d41e2__section_xyk_sqs_dfc"/>

## List All Documents for an Execution

This endpoint allows you to retrieve all documents associated with a specific execution, including the processing statuses of the documents. You must provide the pipeline ID and the execution ID as parameters.

You can list all documents for an execution by using the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}}/documents`.

Populate the code snippet with the following:

-   `{{pipelineId}}`: The pipeline ID
-   `{{executionId}}`: The ID of the specific execution
-   `{{resource_group}}`: The AI resource group ID assigned to your account

This endpoint returns a response in JSON format. The response includes the list of all documents processed during the specified execution.

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}}/documents \  
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Authorization: Bearer {{access_token}}' 
> 
> ```

The available statuses for documents are the following:

-   TO\_BE\_PROCESSED
-   INDEXED
-   REINDEXED
-   DEINDEXED
-   FAILED
-   FAILED\_TO\_BE\_RETRIED
-   TO\_BE\_SCHEDULED



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

`$top` 

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Limits the number of results returned. For example, `$top=10` returns 10 results.

</td>
</tr>
<tr>
<td valign="top">

`$skip` 

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Skips a specific number of results. For example, `$skip=20` skips the first 20.

</td>
</tr>
<tr>
<td valign="top">

`$count` 

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

If `true`, includes the total count in the response. If `false`, includes the total number of records in the response.

</td>
</tr>
</table>

> ### Example:  
> This code returns a JSON array of document objects associated with the pipeline execution.
> 
> ```
> curl --request GET 
>   --url "$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions{{executionId}}/documents?$top=10&$skip=20&$count=true" 
>   --header "AI-Resource-Group: {{resource_group}}" \ 
>   --header 'Authorization: Bearer {{access_token}}'
> ```

The available statuses for documents are the following:

-   TO\_BE\_PROCESSED
-   INDEXED
-   REINDEXED
-   DEINDEXED
-   FAILED
-   FAILED\_TO\_BE\_RETRIED
-   TO\_BE\_SCHEDULED



<a name="copy174102376a3e4032ba82bd81889d41e2__section_f44_rng_qfc"/>

## Get a Specific Document from an Execution

This endpoint allows you to retrieve detailed information for a specific document within an execution, including its processing status. The endpoint requires the input parameters for the pipeline ID, execution ID, and document ID.

You can retrieve a specific document by using the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}}/documents/{{documentID}}`.

Populate the code snippet with the following:

-   `{{pipelineId}}`: The pipeline ID
-   `{{executionId}}`: The ID of the specific execution
-   `{{documentId}}`: The ID of the specific document
-   `{{resource_group}}`: The AI resource group ID assigned to your account
-   `{{access_token}}`: Your access token for SAP AI Core

This endpoint returns a response in JSON format. The response includes the specific document processed during the specified execution. It also includes the document's processing status by pipeline ID, execution ID, and document ID.

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API_URL /v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}}/documents/{{documentID}} \  
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Authorization: Bearer {{access_token}}'
> ```

The available statuses for documents are the following:

-   TO\_BE\_PROCESSED
-   INDEXED
-   REINDEXED
-   DEINDEXED
-   FAILED
-   FAILED\_TO\_BE\_RETRIED
-   TO\_BE\_SCHEDULED



<a name="copy174102376a3e4032ba82bd81889d41e2__section_kfh_s4g_qfc"/>

## List All Documents for a Pipeline

This endpoint allows you to retrieve all documents for a pipeline, including the processing statuses by pipeline ID.

You can retrieve all documents by using the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/documents`.

Populate the code snippet with the following:

-   `{{pipelineId}}`: The pipeline ID
-   `{{resource_group}}`: The AI resource group ID assigned to your account
-   `{{access_token}}`: Your access token for SAP AI Core

This endpoint returns a response in JSON format.

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/documents \
>   --header 'AI-Resource-Group: {{resource_group}}' \ 
>   --header 'Authorization: Bearer {{access_token}}'
> ```

The available statuses for documents are the following:

-   TO\_BE\_PROCESSED
-   INDEXED
-   REINDEXED
-   DEINDEXED
-   FAILED
-   FAILED\_TO\_BE\_RETRIED
-   TO\_BE\_SCHEDULED



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

`$top` 

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Limits the number of results returned. For example, `$top=10` returns 10 results.

</td>
</tr>
<tr>
<td valign="top">

`$skip` 

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Skips a specific number of results. For example, `$skip=20` skips the first 20.

</td>
</tr>
<tr>
<td valign="top">

`$count` 

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

If `true`, includes the total count in the response. If `false`, includes the total number of records in the response.

</td>
</tr>
</table>

> ### Example:  
> This code returns a JSON array of document objects associated with the pipeline execution.
> 
> ```
> curl --request GET 
>   --url "$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/documents?$top=10&$skip=20&$count=true" 
>   --header "AI-Resource-Group: {{resource_group}}"
>   --header 'Authorization: Bearer {{access_token}}'
> ```



<a name="copy174102376a3e4032ba82bd81889d41e2__section_fmd_kpg_qfc"/>

## Get a Specific Document for a Pipeline

This endpoint allows you to retrieve detailed information about a document within a specific pipeline, including the document's processing status. The endpoint requires the pipeline ID and document ID as parameters.

Populate the code snippet with the following:

-   `{{pipelineId}}`: The pipeline ID
-   `{{documentId}}`: The ID of the specific document
-   `{{resource_group}}`: The AI resource group ID assigned to your account
-   `{{access_token}}`: Your access token for SAP AI Core

This endpoint returns a response in JSON format. The response includes the specific document processed in the pipeline.

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/documents/{{documentID}} 
>   --header 'AI-Resource-Group: {{resource_group}}' \ 
>   --header 'Authorization: Bearer {{access_token}}'
> ```

The available statuses for documents are the following:

-   TO\_BE\_PROCESSED
-   INDEXED
-   REINDEXED
-   DEINDEXED
-   FAILED
-   FAILED\_TO\_BE\_RETRIED
-   TO\_BE\_SCHEDULED

