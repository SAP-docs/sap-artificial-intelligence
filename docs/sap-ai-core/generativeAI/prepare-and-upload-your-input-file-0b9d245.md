<!-- loio0b9d245b7db846ff86482c6b56640b21 -->

# Prepare and Upload Your Input File



## Prerequisites

-   You have an object store secret for one of the following providers. Other providers are not supported for batch consumption. For more information, see [Register Your Object Store Secret](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/register-your-object-store-secret?locale=en-US).
    -   Amazon S3
    -   Azure Blob Storage
    -   Google Cloud Storage
    -   Alibaba Cloud OSS
    -   SAP HANA Cloud, Data Lake




## Prepare Your Input File

Batch jobs require a JSON Lines file as input.

Each line must be a self-contained, valid JSON object representing one inference request, and lines must not be separated by commas.

For detailed input file specifications, see the [Azure OpenAI Batch documentation](https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/batch?tabs=global-batch%2Cstandard-input%2Cpython-secure&pivots=rest-api).

**The following fields are required per line:**


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`custom_id`

</td>
<td valign="top">

A unique identifier for the request. Used to match responses to inputs.

</td>
</tr>
<tr>
<td valign="top">

`method`

</td>
<td valign="top">

The HTTP method. The following methods are supported:

-   `POST`



</td>
</tr>
<tr>
<td valign="top">

`url`

</td>
<td valign="top">

The inference endpoint path. The following paths are supported:

-   `/v1/chat/completions`



</td>
</tr>
<tr>
<td valign="top">

`body`

</td>
<td valign="top">

The request body.

The request body must include the following:

-   `model`
-   `messages`

Optionally, the request body can include parameters.

</td>
</tr>
</table>

> ### Note:  
> All requests in the input file must use the same model.

**Example**

```
{"custom_id": "request-1", "method": "POST", "url": "/v1/chat/completions", "body": {"model": "gpt-4.1", "messages": [{"role": "user", "content": "What is machine learning?"}], "max_tokens": 150}}
{"custom_id": "request-2", "method": "POST", "url": "/v1/chat/completions", "body": {"model": "gpt-4.1", "messages": [{"role": "user", "content": "Explain neural networks in simple terms"}], "max_tokens": 150}}

```



## Upload Your Input File

Upload the JSONL input file to your object store. The batch service accesses it using the `ai://` URI scheme, which references a registered object store secret.

The URI format is:

```
ai://<object_store_secret_name>/<file_path>/<file_name>.jsonl
```

Where `<object_store_secret_name>` is the name of the object store secret registered in SAP AI Core.

> ### Note:  
> You will need your full URI when creating the batch job.

For instructions on uploading files to your specific object store, see the documentation from the storage provider.

