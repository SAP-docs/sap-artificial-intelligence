<!-- loioe57dbe56c2d44aabaac6280ae90ee66a -->

# Adding to an Inference Record



## Prerequisites

-   You've made a request to an LLM or orchestration, and included inference recording in your headers. You know the ID of the inference record that you want to access. For more information, see [Record an Inference in Inference Observability](record-an-inference-in-inference-observability-7d493c7.md).

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



## Adding Labels

Send a POST request to the endpoint: `$AI_API/observability/inferences/{{inferenceId}}/labels`. Include the ID of the inference that you want to update in your request. Include your labels as key-value pairs in the body.

> ### Restriction:  
> Only new labels can be added. If you try to add a label with an existing key, the request will be rejected. Label keys must have the prefix `ext.ai.sap.com`.

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API/observability/inferences/{{inferenceId}}/labels \
>   --header 'ai-resource-group: <resource_group>' \
>   --header 'authorization: Bearer $TOKEN' \
>   --header 'content-encoding: application/json' \
>   --header 'content-type: application/json' \
>   --data '[
>   {
>     "key": "ext.ai.sap.com/<key>",
>     "value": "<value>"
>   }
> 
> ```



### Result

Successful requests return a message confirming that the label has been stored with the inference record.

> ### Output Code:  
> ```
> {
>   "message": "inference label stored."
> }
> ```



## Adding Feedback

Send a POST request to the endpoint: `$AI_API/observability/inferences/{{inferenceId}}/feedback`. Include the ID of the inference that you want to update in your request. Include your feedback in the body. The feedback can be any object.

> ### Note:  
> POST requests always add feedback. Existing feedback isn't overwritten.

> ### Output Code:  
> ```
> curl --request POST \
>   --url $AI_API/observability/inferences/{{inferenceId}}/feedback \
>   --header 'ai-resource-group: <resource_group>' \
>   --header 'authorization: Bearer $TOKEN' \
>   --header 'content-encoding: application/json' \
>   --header 'content-type: application/json' \
>   --data '[{ "content": {"stars": 5}}]'
> ```



### Result

Successful requests rerun a message confirming that the feedback has been stored with the inference record.

> ### Output Code:  
> ```
> {
>   "message": "feedback stored."
> }
> ```

