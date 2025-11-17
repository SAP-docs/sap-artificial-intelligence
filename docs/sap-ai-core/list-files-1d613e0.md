<!-- loio1d613e0d1518435fb07b32a70c35345d -->

# List Files

**Parent topic:**[Manage Files](manage-files-386ba71.md "An artifact refers to data or a file that is produced or consumed by executions or deployments. They are managed through SAP AI Core and your connected object store.")

**Related Information**  


[Create Files](create-files-66413f1.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_q4f_f33_tcc"/>

## Procedure

Run the following code:

```
curl --request GET "$AI_API_URL/v2/lm/artifacts" --header "Authorization: Bearer $TOKEN" --header "AI-Resource-Group: $RESOURCE_GROUP"
```



<a name="task_i3h_n13_tcc__result_kfl_1jd_5xb"/>

## Results

> ### Sample Code:  
> ```
> 
> {
>    "count":3,
>    "resources":[
>       {
>          "createdAt":"2021-02-09T08:08:12Z",
>          "description":"",
>          "executionId":"d44edae36c187cf6",
>          "id":"3088b75f-5448-4c19-8055-392668a043ec",
>          "kind":"model",
>          "modifiedAt":"2021-02-09T08:08:12Z",
>          "name":"pytf-model",
>          "scenarioId":"ae0bd260-41ef-4162-81b0-861bd78a8516",
>          "url":"ai://default/d44edae36c187cf6/pytf-model"
>       },
>       {k
>          "createdAt":"2021-02-09T07:56:37Z",
>          "description":"",
>          "executionId":"d44edae36c187cf6",
>          "id":"38f7a46b-454d-4543-9457-b1eede5036f8",
>          "kind":"model",
>          "modifiedAt":"2021-02-09T07:56:37Z",
>          "name":"churn-pickle",
>          "scenarioId":"ae0bd260-41ef-4162-81b0-861bd78a8516",
>          "url":"ai://default/d44edae36c187cf6/churn-pickle"
>       },
>       {
>          "createdAt":"2021-02-07T16:07:16Z",
>          "description":"Churn and Text Classifier Dataset",
>          "id":"b45265f2-9bc3-441a-a0e1-fac1438acb79",
>          "kind":"dataset",
>          "modifiedAt":"2021-02-07T16:07:16Z",
>          "name":"pytf",
>          "scenarioId":"84fe6957-1145-4183-b682-8f11ca56d060",
>          "url":"ai://default/pytf/"
>       }
>    ]
> }
> ```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_mtc_n33_tcc"/>

## Procedure

1.  Send a GET request to the endpoint `{{apiurl}}/v2/lm/artifacts`

2.  On the *Authorization* tab, set the type to *Bearer Token*.

3.  Set the token value to `{{token}}`.

4.  On the *Header* tab, add the following entry:


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
    
    `AI-Resource-Group` 
    
    </td>
    <td valign="top">
    
    *<Name of your resourceGroup\>* \(in the example, `default` is used\)
    
    </td>
    </tr>
    </table>
    
5.  Send the request.


