<!-- loio32536ef88416475e9ea1a433aeae79c1 -->

# Check Batch Status



## Prerequisites

You've created a batch job, and know its ID. For more information, see [Create a Batch Job](create-a-batch-job-bb19774.md).



## Procedure

Batches are processed asynchronously in the background. You can monitor the progress of your batch by sending a GET request to the endpoint: `$AI_API/llm-batch-service/v1/batches/$BATCH_ID/status`. Include your batch ID in your request.

Make sure that you've set the following headers:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. You can set the URL as an environment variable.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl -X GET "$AI_API/llm-batch-service/v1/batches/$BATCH_ID/status" \
>     -H 'AI-Resource-Group: <resource_group>' \
>     -H 'Content-Type: application/json' \
>     -H "Authorization: Bearer $AUTH_TOKEN" \
> ```



## Results

The response includes the current status of your batch.

> ### Output Code:  
> ```
> {
>   "current_status": "IN_PROGRESS",
>   "target_status": "COMPLETED",
>   "updated_at": "2026-01-07T10:35:00Z",
>   "message": "Processing batch requests"
> }
> 
> ```

Statuses include the following:


<table>
<tr>
<th valign="top">

Status

</th>
<th valign="top">

Description

</th>
<th valign="top">

Action

</th>
</tr>
<tr>
<td valign="top">

`PENDING`

</td>
<td valign="top">

Job is queued and waiting to start.

</td>
<td valign="top">

Continue to poll the job status.

</td>
</tr>
<tr>
<td valign="top">

`PREPARING_INPUT`

</td>
<td valign="top">

The system validates and prepares the input file for the LLM provider.

</td>
<td valign="top">

Continue to poll the job status.

</td>
</tr>
<tr>
<td valign="top">

`INPUT_PREPARED`

</td>
<td valign="top">

The input file is ready. The system will submit the job to the provider.

</td>
<td valign="top">

Continue to poll the job status.

</td>
</tr>
<tr>
<td valign="top">

`IN_PROGRESS`

</td>
<td valign="top">

The LLM provider is processing the job.

</td>
<td valign="top">

Continue to poll the job status.

</td>
</tr>
<tr>
<td valign="top">

`PREPARING_OUTPUT`

</td>
<td valign="top">

Processing is complete. The system writes output files to the object store.

</td>
<td valign="top">

Continue to poll the job status.

</td>
</tr>
<tr>
<td valign="top">

`COMPLETED`

</td>
<td valign="top">

The job finished successfully. Output files are available.

</td>
<td valign="top">

Retrieve the results from the object store.

</td>
</tr>
<tr>
<td valign="top">

`FAILED`

</td>
<td valign="top">

The job failed due to an error.

</td>
<td valign="top">

Check the `message` field and retry if appropriate.

</td>
</tr>
<tr>
<td valign="top">

`CANCELLING`

</td>
<td valign="top">

The system is cancelling the job and cleaning up resources.

</td>
<td valign="top">

Continue to poll the job status.

</td>
</tr>
<tr>
<td valign="top">

`CANCELLED`

</td>
<td valign="top">

Job was cancelled by the user.

</td>
<td valign="top">

No action is required.

</td>
</tr>
</table>



## Next Steps

When your batch is `COMPLETED`, you can view the output in your object store. For more information, see [Retrieve Results](retrieve-results-7d18a48.md).

