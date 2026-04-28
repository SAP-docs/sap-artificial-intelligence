<!-- loio04c4e0e6531f4acda8c1c14321fb1809 -->

# Retrieving an Inference Record

You can retrieve inference records individually by ID, or by retrieving multiple records associated with a predefined label.



## Prerequisites

-   You've made a request to an LLM or orchestration, and included inference recording in your headers. For more information, see [Record an Inference in Inference Observability](record-an-inference-in-inference-observability-7d493c7.md).
-   You know the ID of the inference record that you want to access, or you've included labels in your record. For more information, see [Record an Inference in Inference Observability](record-an-inference-in-inference-observability-7d493c7.md) and [Adding to an Inference Record](adding-to-an-inference-record-e57dbe5.md).

Ensure that you have the following headers set:


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

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
</table>



## Retrieve an Inference Record by ID

Send a GET request to the endpoint: `$AI_API/observability/inferences/{{inferenceId}}`. Include the ID of the inference that you want to retrieve in your request.

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API/observability/inferences/{{inferenceId}} \
>   --header 'ai-resource-group: <resource_group>' \
>   --header 'authorization: Bearer $TOKEN' \
>   --header 'content-type: application/json'
> ```



### Result

For responses with `ai-inference-observability-persistence-mode` set to `full`: the response contains metadata, the request and response, and any labels or feedback added to the inference.

> ### Output Code:  
> ```
> {
>   "id": "4ba60b4a-30ee-9070-9671-3fbca68ed085",
>   "source": "llmaccess",
>   "resourceGroup": "default",
>   "deploymentId": "d64b3328cf209947",
>   "modelName": "gpt-4o",
>   "modelVersion": "2024-08-06",
>   "streaming": true,
>   "responseHttpCode": 200,
>   "inputTokens": 21,
>   "outputTokens": 15,
>   "latency": 637.341,
>   "createdAt": "2026-03-11T11:48:24.3133655Z",
>   "objectStoreSecretName": "inference-observability-store",
>   "request": "{\"url\": \"http://rg-openai-exploration-us.openai.azure.com/openai/deployments/gpt-4o-2024-08-06/chat/completions?api-version=2025-03-01-preview\", \"headers\": {\"Content-Type\": \"application/json\", \"api-key\": \"7f32c2cf9bf645e3b5cc0df2943b35bc\"}, \"body\": \"{\\\"messages\\\": [{\\\"role\\\": \\\"system\\\", \\\"content\\\": \\\"You are a helpful assistant.\\\"}, {\\\"role\\\": \\\"user\\\", \\\"content\\\": \\\"Tell me a joke\\\"}], \\\"temperature\\\": 1, \\\"stream\\\": true}\"}",
>   "response": "{\"choices\":[],\"created\":0,\"id\":\"\",\"model\":\"\",\"object\":\"\",\"prompt_filter_results\":[{\"prompt_index\":0,\"content_filter_results\":{\"hate\":{\"filtered\":false,\"severity\":\"safe\"},\"self_harm\":{\"filtered\":false,\"severity\":\"safe\"},\"sexual\":{\"filtered\":false,\"severity\":\"safe\"},\"violence\":{\"filtered\":false,\"severity\":\"safe\"}}}]}, 
> [ … ]
> }
> 
> 
> ```

> ### Note:  
> If the associated object store secret isn't valid or can't be retrieved, only the metadata will be returned.



## Retrieve Inference Records Using Labels

You can retrieve inferences by label key only, or using label key-value pairs.

Send a GET request to the endpoint: `$AI_API/observability/inferences?labelSelector=ext.ai.sap.com/<key>=<value>`. Include the key or key-value pair that you want to retrieve in your request.

The following example shows a request for `key`: *<medium\>* and `value`: *<mobile\>*:

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API/observability/inferences?labelSelector=ext.ai.sap.com/medium=Mobile \
>   --header 'ai-resource-group: <resource_group>' \
>   --header 'authorization: Bearer $TOKEN' \
>   --header 'content-type: application/json'
> ```



### Result

The result includes a list of all matching inference records, and all associated labels and feedback:

> ### Output Code:  
> ```
> {
>   "count": 10,
>   "resources": [
>     {
>       "id": "4ba60b4a-30ee-9070-9671-3fbca68ed085",
>       "labels": [
>         {
>           "key": "ext.ai.sap.com/use-case",
>           "value": "Accounting"
>         },
>         {
>           "key": "ext.ai.sap.com/medium",
>           "value": "Mobile"
>         }
>       ],
>       "source": "llmaccess",
>       "resourceGroup": "default",
>       "deploymentId": "d64b3328cf209947",
>       "modelName": "gpt-4o",
>       "modelVersion": "2024-08-06",
>       "streaming": true,
>       "responseHttpCode": 200,
>       "inputTokens": 21,
>       "outputTokens": 15,
>       "latency": 637.341,
>       "createdAt": "2026-03-11T11:48:24.3133655Z",
>       "objectStoreSecretName": "default",
>       "feedback": [
>         {
>           "content": {
>             "stars": 5
>           }
>         }
>       ]
>       "request": "{\"url\": \"http://rg-openai-exploration-us.openai.azure.com/openai/deployments/gpt-4o-2024-08-06/chat/completions?api-version=2025-03-01-preview\", \"headers\": {\"Content-Type\": \"application/json\", \"api-key\": \"7f32c2cf9bf645e3b5cc0df2943b35bc\"}, \"body\": \"{\\\"messages\\\": [{\\\"role\\\": \\\"system\\\", \\\"content\\\": \\\"You are a helpful assistant.\\\"}, {\\\"role\\\": \\\"user\\\", \\\"content\\\": \\\"Tell me a joke\\\"}], \\\"temperature\\\": 1, \\\"stream\\\": true}\"}",
>       "response": "{\"choices\":[],\"created\":0,\"id\":\"\",\"model\":\"\",\"object\":\"\",\"prompt_filter_results\":[{\"prompt_index\":0,\"content_filter_results\":{\"hate\":{\"filtered\":false,\"severity\":\"safe\"},\"self_harm\":{\"filtered\":false,\"severity\":\"safe\"},\"sexual\":{\"filtered\":false,\"severity\":\"safe\"},\"violence\":{\"filtered\":false,\"severity\":\"safe\"}}}]}, 
> [….]
> 
> ```

