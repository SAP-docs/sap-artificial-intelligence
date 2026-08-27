<!-- loioe3723c2e5a854da98c9b94ca344350fc -->

# Delete a Batch Job

Deleting a job removes its metadata from the service. Output files in the object store are not affected.

> ### Restriction:  
> Only batch jobs in `COMPLETED`, `FAILED`, or `CANCELLED` state can be deleted. To check the status of your cancellation, see [Check Batch Status](check-batch-status-32536ef.md).

To delete a batch job and its associated metadata, send a DELETE request to the endpoint: `$AI_API/llm-batch-service/v1/batches/$BATCH_ID`. Include your batch ID in your request.

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

```
curl -X DELETE "$$AI_API/llm-batch-service/v1/batches/$BATCH_ID" \
    -H 'AI-Resource-Group: <resource_group>' \
    -H 'Content-Type: application/json' \
    -H "Authorization: Bearer $AUTH_TOKEN" \
```

