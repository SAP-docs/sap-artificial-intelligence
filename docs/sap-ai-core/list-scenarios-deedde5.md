<!-- loiodeedde5c7def40eab20d0e04edfee4b5 -->

# List Scenarios

A scenario is an implementation of a specific AI use case within a user's tenant. It consists of a pre-defined set of AI capabilities in the form of executables and templates.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## List Scenarios Using Curl



<a name="task_i3h_n13_tcc__steps_c1w_2z3_tcc"/>

## Procedure

Run the following code:

```
curl --request GET "$AI_API_URL/v2/lm/scenarios" --header "Authorization: Bearer $TOKEN" --header "AI-Resource-Group: $RESOURCE_GROUP"
```



<a name="task_i3h_n13_tcc__result_scr_tjj_wxb"/>

## Results

> ### Output Code:  
> ```json
> {
>    "count":2,
>    "resources":[
>       {
>          "createdAt":"2021-02-03T18:38:32+00:00",
>          "description":"churn and text class scenario desc",
>          "id":"84fe6957-1145-4183-b682-8f11ca56d060",
>          "labels":[
>             
>          ],
>          "modifiedAt":"2021-02-04T11:14:02+00:00",
>          "name":"churntextclassscenname"
>       },
>       {
>          "createdAt":"2021-02-04T14:11:02+00:00",
>          "description":"churn and text class scenario desc",
>          "id":"ae0bd260-41ef-4162-81b0-861bd78a8516",
>          "labels":[
>             
>          ],
>          "modifiedAt":"2021-02-09T07:35:03+00:00",
>          "name":"churntextclassscenname"
>       }
>    ]
> } 
> ```

> ### Note:  
> Only scenarios that have a defined training executable can be created. When a new scenario ID is specified in the workflow template for a training executable, a new scenario will be created along with the training executable.
> 
> For now, a new scenario with only a deployment executable cannot be created. A possible work-around is to create a scenario with a dummy training executable and then use the same scenario ID in the serving template.

<a name="task_iq1_d1j_tcc"/>

<!-- task\_iq1\_d1j\_tcc -->

## Get Scenario Versions Using Curl



<a name="task_iq1_d1j_tcc__steps_jq1_d1j_tcc"/>

## Procedure

Run the following code:

```
curl --location --request GET '$API_URL/v2/lm/scenarios/$SCENARIO_ID/versions' \
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## List Scenarios Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_dmf_4z3_tcc"/>

## Procedure

1.  Send GET request to the endpoint `{{apiurl}}/v2/lm/scenarios`

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
    
    *<Name of your resourceGroup\>* 
    
    </td>
    </tr>
    </table>
    
5.  Send the request.

    > ### Note:  
    > Only scenarios that have a defined training executable can be created. When a new scenario ID is specified in the workflow template for a training executable, a new scenario will be created along with the training executable.
    > 
    > For now, a new scenario with only a deployment executable cannot be created. A possible work-around is to create a scenario with a dummy training executable and then use the same scenario ID in the serving template.


<a name="task_b3y_rz3_tcc"/>

<!-- task\_b3y\_rz3\_tcc -->

## Get Scenario Versions Using a Third-Party API Platform



<a name="task_b3y_rz3_tcc__steps_c3y_rz3_tcc"/>

## Procedure

Create a new GET request and enter the URL `{{apiurl}}/v2/lm/scenarios/{{scenarioid}}/versions`

