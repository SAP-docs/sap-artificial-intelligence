<!-- loiodeedde5c7def40eab20d0e04edfee4b5 -->

# List Scenarios

A scenario is an implementation of a specific AI use case within a user's tenant. It consists of a pre-defined set of AI capabilities in the form of executables and templates.

**Parent topic:**[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Workflow Templates](workflow-templates-83523ab.md "Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.")

[List Executables](list-executables-80895a4.md "An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts (datasets or models) and parameters (custom key-pair values) that enable the template to be reused in different scenarios.")

[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references (such as datasets or models), and environment settings that are used to instantiate and run an execution or deployment of an executable or template.")

[List Configurations](list-configurations-8074b2a.md "")

[Using Artifact Signatures](using-artifact-signatures-2f02a1d.md "Artifact signatures in the form of a hash can be added to output artifacts from executions.")

[Start Training](start-training-54b44e4.md "")

[Stop Training Instances](stop-training-instances-3d85344.md "")

[Delete Training Instances](delete-training-instances-612ce17.md "")

[Efficiency Features](efficiency-features-4cb76f7.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "Deployment and execution logs contain information about API processing and metrics.")

[Training Schedules](training-schedules-2b702f8.md "")

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

