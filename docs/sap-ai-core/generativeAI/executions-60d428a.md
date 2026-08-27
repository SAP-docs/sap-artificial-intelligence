<!-- copy60d428a704064dad926c4ca101550afa -->

# Executions

You can get the details of your executions in data pipelines using the following endpoints:



<a name="copy60d428a704064dad926c4ca101550afa__section_z4q_rqs_dfc"/>

## List All Executions of a Document Grounding Pipeline

This endpoint allows you to list all executions associated with a specific document grounding pipeline. The response includes execution metadata such as status, timestamps, and identifiers.

You can list all the executions by using the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions?lastExecution=false`.

Populate the code snippet with the following:

-   `{{pipelineId}}`: The ID of the pipeline whose executions you want to list
-   `lastExecution`: Set to `true` to fetch only the latest execution \(the default value is `false`\)
-   `{{resource_group}}`: The AI resource group ID assigned to your account
-   `{{access_token}}`: Your access token for SAP AI Core

This endpoint returns a response in JSON format.

> ### Sample Code:  
> ```
> curl --request GET \
>   --url "$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions?lastExecution=false" \
>   --header "AI-Resource-Group: {{resource_group}}"
>   --header 'Authorization: Bearer {{access_token}}'
> ```



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
> This code returns a JSON array of pipeline execution objects.
> 
> ```
> curl --request GET 
>   --url "$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions?$top=10&$skip=20&$count=true" 
>   --header "AI-Resource-Group: {{resource_group}}"
>   --header 'Authorization: Bearer {{access_token}}'
> ```

Available statuses for executions are as follows:

-   NEW
-   UNKNOWN
-   INPROGRESS
-   FINISHED
-   FINISHEDWITHERRORS
-   TIMEOUT



<a name="copy60d428a704064dad926c4ca101550afa__section_hxd_q3g_qfc"/>

## Get Specific Execution Details

This endpoint allows you to retrieve the details of a specific execution of a document grounding pipeline by providing the pipeline ID and execution ID.

You can retrieve a specific execution by using the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}}`.

Populate the code snippet with the following:

-   `{{pipelineId}}`: The ID of the pipeline that contains the execution that you want to retrieve
-   `{{executionId}}`: The ID of the specific execution
-   `{{resource_group}}`: The AI resource group ID assigned to your account
-   `{{access_token}}`: Your access token for SAP AI Core

This endpoint returns a response in JSON format. The response includes fields such as `status`, `startTime`, `endTime`, and any `errorMessage`.

> ### Sample Code:  
> ```
> curl --request GET \
>   --url "$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}}" \
>   --header "AI-Resource-Group: {{resource_group}}"
>   --header 'Authorization: Bearer {{access_token}}'
> ```

Available statuses for executions are as follows:

-   NEW
-   UNKNOWN
-   INPROGRESS
-   FINISHED
-   FINISHEDWITHERRORS
-   TIMEOUT

