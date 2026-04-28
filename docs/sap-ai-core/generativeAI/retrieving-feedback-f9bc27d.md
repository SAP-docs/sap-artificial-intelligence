<!-- loiof9bc27d0e5834ab5aa27dacce7836c9b -->

# Retrieving Feedback

You can retrieve all stored feedback of an inference record.



## Prerequisites

-   You've made a request to an LLM or orchestration, and included inference recording in your headers, and you know the ID of the inference record that you want to access. For more information, see [Record an Inference in Inference Observability](record-an-inference-in-inference-observability-7d493c7.md).
-   You've added feedback to your record. For more information, see [Adding to an Inference Record](adding-to-an-inference-record-e57dbe5.md).

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



## Procedure

Send a GET request to the endpoint: `$AI_API/observability/inferences/{{inferenceId}}/feedback`. Include the ID of the inference that you want to retrieve in your request.

> ### Sample Code:  
> ```
> 
> curl --request GET \
>   --url $AI_API/observability/inferences/{{inferenceId}}/feedback \
>   --header 'ai-resource-group: <resource_group>' \
>   --header 'authorization: Bearer $TOKEN' \
>   --header 'content-encoding: application/json'
> ```



## Results

The result is a list of all stored feedback objects.

> ### Output Code:  
> ```
> {
>   "count": 1,
>   "resources": [
>     {
>       "content": {
>         "stars": 5
>       }
>   ]
> }
> ```

