<!-- loiobb1977479f054e8da13426ba3ea7c23f -->

# Create a Batch Job



## Prerequisites

You've prepared and uploaded your batch input file. For more information, see [Prepare and Upload Your Input File](prepare-and-upload-your-input-file-0b9d245.md).



## Procedure

Submit a batch job by sending a POST request to the endpoint `$AI_API/llm-batch-service/v1/batches`.

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

Include the following in your request:


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

`type`

</td>
<td valign="top">

string

</td>
<td valign="top">

Batch processing type. The following values are supported:

-   `llm-native`



</td>
</tr>
<tr>
<td valign="top">

`input.uri`

</td>
<td valign="top">

string

</td>
<td valign="top">

URI of the input file in the object store, The following file types are supported:

-   `.jsonl`



</td>
</tr>
<tr>
<td valign="top">

`output.uri`

</td>
<td valign="top">

string

</td>
<td valign="top">

URI of the output directory in the object store. Must end with `/`.

</td>
</tr>
<tr>
<td valign="top">

`spec.provider`

</td>
<td valign="top">

string

</td>
<td valign="top">

LLM provider. The following providers are supported:

-   `azure-openai`



</td>
</tr>
<tr>
<td valign="top">

`spec.model`

</td>
<td valign="top">

string

</td>
<td valign="top">

Model name.

> ### Note:  
> The model must match the value specified in the input file.



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl -X POST "$AI_API/llm-batch-service/v1/batches" \
>     -H 'AI-Resource-Group: <resource_group>' \
>     -H 'Content-Type: application/json' \
>     -H "Authorization: Bearer $AUTH_TOKEN" \
>     -D '{
>         "type": "llm-native",
>         "input": {
>             "uri": "ai://<object_store_secret_name>/<input_file>.jsonl"
>         },
>         "output": {
>             "uri": "ai://<object_store_secret_name>/<output_folder>/"
>         },
>         "spec": {
>             "provider": "azure-openai",
>             "model": "gpt-4.1"
>         }
>     }'
> 
> ```



## Results

The service schedules the job for processing and returns a unique batch ID.

> ### Output Code:  
> ```
> {
>   "id": "550e8400-e29b-41d4-a716-446655440000",
>   "created_at": "2026-01-07T10:30:00Z",
>   "status": "PENDING",
>   "message": "Batch job scheduled"
> }
> 
> ```



## Next Steps

Use your batch ID to check the status of your batch, and retrieve your results. For more information, see [Check Batch Status](check-batch-status-32536ef.md) and [Retrieve Results](retrieve-results-7d18a48.md).

