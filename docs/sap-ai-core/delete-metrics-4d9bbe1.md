<!-- loio4d9bbe171064468486a432258ce41761 -->

# Delete Metrics



You can delete metrics by submitting a DELETE request to the endpoint `/v2/lm/metrics`. To delete tracking data, you must provide the following parameters:

-   `AI-Resource-Group` \(header\) – string
-   `executionId` \(query\)

**Query Parameters**


<table>
<tr>
<th valign="top">

Parameter

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

`executionIds`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Array of String

</td>
<td valign="top">

ID of execution

</td>
</tr>
</table>

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
</table>



<a name="loio4d9bbe171064468486a432258ce41761__section_b1k_cql_sxb"/>

## Responses of DELETE API


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

Metric resource was successfully deleted

</td>
</tr>
<tr>
<td valign="top">

404

</td>
<td valign="top">

The specified resource was not found

</td>
</tr>
</table>

> ### Sample Code:  
> Sample 404 response:
> 
> ```
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
> ```

<a name="task_qkl_2pl_sxb"/>

<!-- task\_qkl\_2pl\_sxb -->

## Deleting Metrics with Postman



<a name="task_qkl_2pl_sxb__steps_wsf_pql_sxb"/>

## Procedure

1.  Send a DELETE request to the endpoint `{{apiurl}}/v2/lm/metrics`

2.  On the *Authorization* tab, set the type to *Bearer Token*.

3.  Set the token value to `{{token}}`.

4.  Set the query parameters in *Params*.


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
    
    executionId
    
    </td>
    <td valign="top">
    
    \{\{executionId\}\}
    
    </td>
    </tr>
    </table>
    
5.  Set the *Header*.


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
    
    <Your Resource Group name\>
    
    </td>
    </tr>
    </table>
    
6.  Send the request.




<a name="task_qkl_2pl_sxb__result_rkx_bsl_sxb"/>

## Results

You should receive the message ***Metric Resource was successfully deleted***.

<a name="task_kzx_fqf_scc"/>

<!-- task\_kzx\_fqf\_scc -->

## Deleting Metrics with curl



<a name="task_kzx_fqf_scc__steps_abc_def_ghi"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/lm/metrics` with the required query parameters and headers.

```

curl --location --request DELETE '$AI_API_URL/v2/lm/metrics?executionId=e1c49497ccf6dde8' \
--header 'AI-Resource-Group: default' \
--header 'Authorization: Bearer $TOKEN'
```

