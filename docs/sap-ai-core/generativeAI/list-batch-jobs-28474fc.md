<!-- loio28474fced12843c99e9ebf733d06e329 -->

# List Batch Jobs



To list all batch jobs for the current tenant and resource group, send a GET request to the endpoint: `$AI_API/llm-batch-service/v1/batches`.

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
> curl -X GET "$AI_API/llm-batch-service/v1/batches" \
>     -H 'AI-Resource-Group: <resource_group>' \
>     -H 'Content-Type: application/json' \
>     -H "Authorization: Bearer $AUTH_TOKEN" \
> ```

> ### Output Code:  
> ```
> {
>   "count": 2,
>   "resources": [
>     {
>       "id": "550e8400-e29b-41d4-a716-446655440000",
>       "type": "llm-native",
>       "provider": "azure-openai",
>       "created_at": "2026-01-07T10:30:00Z",
>       "status": "COMPLETED"
>     },
>     {
>       "id": "661f9511-f3ac-52e5-b827-557766551111",
>       "type": "llm-native",
>       "provider": "azure-openai",
>       "created_at": "2026-01-07T11:00:00Z",
>       "status": "IN_PROGRESS"
>     }
>   ]
> }
> 
> ```

