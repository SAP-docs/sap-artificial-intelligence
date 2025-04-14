<!-- loio77e386ef2eca48838dba7d33b595923e -->

# Patch Metrics

<a name="task_wl3_kpf_scc"/>

<!-- task\_wl3\_kpf\_scc -->

## Patching Metrics Using a Third-Party API Platform



<a name="task_wl3_kpf_scc__steps_wjs_mpf_scc"/>

## Procedure

1.  Prepare a PATCH request to the endpoint `{{apiurl}}/v2/lm/metrics` with the following headers:

    **Header**


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Required
    
    </th>
    <th valign="top">

    Data Type
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `AI-Resource-Group`
    
    </td>
    <td valign="top">
    
    Yes
    
    </td>
    <td valign="top">
    
    String
    
    </td>
    <td valign="top">
    
    ID of the resource group that contains the execution.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Content-Type`
    
    </td>
    <td valign="top">
    
    Yes
    
    </td>
    <td valign="top">
    
    value = `application/merge-patch+json`
    
    </td>
    <td valign="top">
    
     
    
    </td>
    </tr>
    </table>
    
2.  On the *Authorization* tab, set the type to *Bearer Token*.

3.  Set the token value to `{{token}}`.

4.  Set the *Header*.


    <table>
    <tr>
    <th valign="top">

    Key
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    AI-Resource-Group
    
    </td>
    <td valign="top">
    
    <Your resource group name\>
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Content-Type
    
    </td>
    <td valign="top">
    
    <Your content type\>
    
    </td>
    </tr>
    </table>
    
5.  Add the *Body*.

    > ### Sample Code:  
    > ```json
    > 
    > {
    >   "executionId": "{{executionid}}",
    >   "metrics": [
    >   {
    >     "name": "Error Rate",
    >     "value": 0.98,
    >     "timestamp": "2021-06-28T07:50:24.589Z",
    >     "step": 2,
    >     "labels": [
    >       {
    >         "name": "group",
    >         "value": "tree-82"
    >       }
    >     ]
    >   }
    >   ],
    >   "tags": [
    >     {
    >       "name": "Artifact Group",
    >       "value": "RFC-1"
    >     }
    >   ],
    >   "customInfo": [
    >     {
    >       "name": "Confusion Matrix",
    >       "value": "[{'Predicted': 'False', 'Actual': 'False','value': 34},{'Predicted': 'False','Actual': 'True', 'value': 124}, {'Predicted': 'True','Actual': 'False','value': 165},{ 'Predicted': 'True','Actual': 'True','value': 36}]"
    >     }
    >   ]
    > }
    > ```

6.  Send the request.




<a name="task_wl3_kpf_scc__result_ymh_4gl_sxb"/>

## Results

As the response, you will receive a 204 \(no content\) response.

<a name="task_yyd_npf_scc"/>

<!-- task\_yyd\_npf\_scc -->

## Patching Metrics Using curl



<a name="task_yyd_npf_scc__steps_bfq_ppf_scc"/>

## Procedure

Run the following code:

```

curl --location --request GET '$AI_API_URL/v2/lm/metrics?executionId=e1c49497ccf6dde8' \
--header 'AI-Resource-Group: default' \
--header 'Authorization: Bearer $TOKEN'
\
--data-raw '{
"executionId": "e1c49497ccf6dde8",
"metrics": [
{
"name": "Error Rate",
"value": 0.98,
"timestamp": "2021-06-28T07:50:24.589Z",
"step": 2,
"labels": [
{
"name": "group",
"value": "tree-82"
}
]
}
],
"tags": [
{
"name": "Artifact Group",
"value": "RFC-1"
}
],
"customInfo": [
{
"name": "Confusion Matrix",
"value": "[{'\''Predicted'\'': '\''False'\'', '\''Actual'\'': '\''False'\'','\''value'\'': 34},{'\''Predicted'\'': '\''False'\'','\''Actual'\'': '\''True'\'', '\''value'\'': 124}, {'\''Predicted'\'': '\''True'\'','\''Actual'\'': '\''False'\'','\''value'\'': 165},{ '\''Predicted'\'': '\''True'\'','\''Actual'\'': '\''True'\'','\''value'\'': 36}]"
}
]
}'
```

