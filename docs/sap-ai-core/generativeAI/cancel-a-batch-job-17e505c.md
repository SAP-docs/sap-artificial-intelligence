<!-- loio17e505c7acd44b5cba363f9449504d55 -->

# Cancel a Batch Job



To cancel a batch job that is in a non-terminal state, for example `PENDING` or `IN_PROGRESS`, send a PATCH request to the endpoint: `$AI_API/llm-batch-service/v1/batches/$BATCH_ID/cancel`. Include your batch ID in your request.

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
> curl -X PATCH "$AI_API/llm-batch-service/v1/batches/$BATCH_ID/cancel" \
>     -H 'AI-Resource-Group: <resource_group>' \
>     -H 'Content-Type: application/json' \
>     -H "Authorization: Bearer $AUTH_TOKEN" \
> ```

> ### Note:  
> Cancellation is asynchronous. The job transitions to `CANCELLED` status after any in-flight provider requests have been terminated. To check the status of your cancellation, see [Check Batch Status](check-batch-status-32536ef.md).

