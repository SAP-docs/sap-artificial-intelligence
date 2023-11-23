<!-- loiof25046fbda39417b8bc66991606b428d -->

# Query Metric Data



You can query metrics by submitting a GET request to the endpoint `/v2/lm/metrics`. To fetch the tracking data, you can use the following parameters:

-   `AI-Resource-Group` \(header\) - string – UUID
-   `executionIds` \(query\) – string – Retrieve metrics based on up to 10 execution IDs \(comma-separated list\)
-   `$select` \(query\) – Selectively retrieve metric resource data, such as metrics and custom info. For example, if the parameter value is a wildcard \(`*`\), then all metric resource data is returned. If the parameter value is `custom info`, then only custom info data is returned. Values should be entered as an array. Only the values `metrics`, `tags`, `customInfo` and `*` are supported.



<a name="loiof25046fbda39417b8bc66991606b428d__section_wy1_xrf_ynb"/>

## Examples



### Responses of GET API

In this example, the `$select` parameter value is a wildcard \(\*\), so all metric resource data is returned.


<table>
<tr>
<th valign="top">

Response Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

List of tracking metadata, where each item includes metrics, labels, parameters, and tags.

</td>
</tr>
</table>

> ### Sample Code:  
> ```json
> {
>   "count": 1,
>   "resources": [
>     {
>       "executionId": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "metrics": [
>         {
>           "name": "Error Rate",
>           "value": 0.98,
>           "timestamp": "2020-11-12T12:36:13.730Z",
>           "step": 2,
>           "labels": [
>             {
>               "name": "group",
>               "value": "tree-82"
>             }
>           ]
>         }
>       ],
>       "tags": [
>         {
>           "name": "Artifact Group",
>           "value": "RFC-1"
>         }
>       ],
>       "customInfo": [
>         {
>           "name": "Confusion Matrix",
>           "value": "[{'Predicted': 'False',  'Actual': 'False','value': 34},{'Predicted': 'False','Actual': 'True',  'value': 124}, {'Predicted': 'True','Actual': 'False','value': 165},{  'Predicted': 'True','Actual': 'True','value': 36}]"
>         }
>       ]
>     }
>   ]
> }
> 
> ```


<table>
<tr>
<th valign="top">

Response Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

The specification of the resource was incorrect.

</td>
</tr>
</table>

> ### Sample Code:  
> ```json
> {
>   "error": {
>     "code": "<error code>",
>     "message": "<error message>.",
>     "requestId": "9832bf934f3743v3948v3",
>     "target": "/metrics",
>     "details": [
>       {
>         "code": "<error code>",
>         "message": "<error message>."
>       }
>     ]
>   }
> }
> 
> ```


<table>
<tr>
<th valign="top">

Response Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

501

</td>
<td valign="top">

The operation is not supported.

</td>
</tr>
</table>

> ### Sample Code:  
> ```json
> {
>   "error": {
>     "code": "02010055",
>     "message": "Metrics was not found.",
>     "requestId": "9832bf934f3743v3948v3",
>     "target": "/metrics",
>     "details": [
>       {
>         "code": "9827389374",
>         "message": "Empty result set."
>       }
>     ]
>   }
> }
> 
> ```

