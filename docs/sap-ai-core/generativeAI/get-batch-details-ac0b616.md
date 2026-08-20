<!-- loioac0b616ccf934311821c817c92ae4016 -->

# Get Batch Details



You can retrieve the full details of a batch job, including input and output URIs, provider, model, and current status by sending a GET request to the endpoint:`$AI_API/llm-batch-service/v1/batches/$BATCH_ID`. Include the batch ID in your request.

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
> curl -X GET "$AI_API/llm-batch-service/v1/batches/$BATCH_ID" \
>     -H 'AI-Resource-Group: <resource_group>' \
>     -H 'Content-Type: application/json' \
>     -H "Authorization: Bearer $AUTH_TOKEN" \
> ```

> ### Output Code:  
> ```
> {
>   "id": "550e8400-e29b-41d4-a716-446655440000",
>   "type": "llm-native",
>   "provider": "azure-openai",
>   "created_at": "2026-01-07T10:30:00Z",
>   "input": {
>     "uri": "ai://my-object-store/input/input-batch.jsonl"
>   },
>   "output": {
>     "uri": "ai://my-object-store/output/"
>   },
>   "spec": {
>     "model": "gpt-4.1"
>   },
>   "status": {
>     "current_status": "COMPLETED",
>     "target_status": "COMPLETED",
>     "updated_at": "2026-01-07T10:45:00Z",
>     "message": "Batch job completed successfully"
>   }
> }
> 
> ```

