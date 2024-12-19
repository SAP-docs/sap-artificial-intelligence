<!-- loio80895a495b4a466b8976735995e23753 -->

# List Executables

An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts \(datasets or models\) and parameters \(custom key-pair values\) that enable the template to be reused in different scenarios.

**Parent topic:**[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Workflow Templates](workflow-templates-83523ab.md "Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.")

[List Scenarios](list-scenarios-deedde5.md "A scenario is an implementation of a specific AI use case within a user's tenant. It consists of a pre-defined set of AI capabilities in the form of executables and templates.")

[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references (such as datasets or models), and environment settings that are used to instantiate and run an execution or deployment of an executable or template.")

[List Configurations](list-configurations-8074b2a.md "")

[Using Artifact Signatures](using-artifact-signatures-2f02a1d.md "Artifact signatures in the form of a hash can be added to output artifacts from executions.")

[Start Training](start-training-54b44e4.md "")

[Stop Training Instances](stop-training-instances-3d85344.md "")

[Delete Training Instances](delete-training-instances-612ce17.md "")

[Efficiency Features](efficiency-features-4cb76f7.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "accessed in the deployment and execution logs.")

[Training Schedules](training-schedules-2b702f8.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## List Executables Using Curl



<a name="task_i3h_n13_tcc__steps_jyt_vcp_tcc"/>

## Procedure

Run the following code:

```
curl --request GET "$AI_API_URL/v2/lm/scenarios" --header "Authorization: Bearer $TOKEN" --header "ai-resource-group: $RESOURCE_GROUP"
```



<a name="task_i3h_n13_tcc__result_bqx_ypj_wxbp"/>

## Results

> ### Output Code:  
> ```json
> {
>    "count":4,
>    "resources":[
>       {
>          "createdAt":"2021-02-04T13:11:01+00:00",
>          "deployable":true,
>          "description":"churn n text class serving executable desc",
>          "id":"pytf-serving",
>          "inputArtifacts":[
>             {
>                "name":"model_uri"
>             }
>          ],
>          "labels":[
>             
>          ],
>          "modifiedAt":"2021-02-04T13:11:01+00:00",
>          "name":"churntextclassexecname",
>          "parameters":[
>             {
>                "name":"modelName",
>                "type":"string",
>                 "default": "value",
>                 "description": "description of the parameter"
>             }
>          ],
>          "scenarioId":"ae0bd260-41ef-4162-81b0-861bd78a8516",
>          "versionId":"0.0.1"
>       },
>       {
>          "createdAt":"2021-02-09T07:35:02+00:00",
>          "deployable":true,
>          "description":"churn n text class serving executable desc",
>          "id":"pytf-serving-tracking",
>          "inputArtifacts":[
>             {
>                "name":"textmodel",
>                "kind": "model",
>                "description": "artifact description",
>                "labels": [
>                   {
>                     "key": "ext.ai.sap.com/customkey1",
>                     "value": "customvalue1"
>                   },
>                   {
>                    "key": "ext.ai.sap.com/customkey2",
>                    "value": "customvalue2"
>                  }
>                ]
>             }
>          ],
>          "labels":[
>             
>          ],
>          "modifiedAt":"2021-02-09T07:35:02+00:00",
>          "name":"churntextclassexecname",
>          "parameters":[
>             {
>                "name":"modelName",
>                "type":"string"
>             }
>          ],
>          "scenarioId":"ae0bd260-41ef-4162-81b0-861bd78a8516",
>          "versionId":"0.0.1"
>       },
>       {
>          "createdAt":"2021-02-09T07:35:03+00:00",
>          "deployable":false,
>          "description":"churn and text class executable desc",
>          "id":"pytf-training-tracking",
>          "inputArtifacts":[
>             {
>                "name":"churn-data"
>             },
>             {
>                "name":"textclass-data"
>             }
>          ],
>          "labels":[
>             
>          ],
>          "modifiedAt":"2021-02-09T07:35:03+00:00",
>          "name":"churnntextclassexecutablename",
>          "outputArtifacts":[
>             {
>                "name":"churn-pickle",
>                "kind": "model",
>                "description": "artifact description",
>                "labels": [
>                  {
>                    "key": "ext.ai.sap.com/customkey1",
>                    "value": "customvalue1"
>                  },
>                  {
>                   "key": "ext.ai.sap.com/customkey2",
>                   "value": "customvalue2"
>                 }
>               ]
>             },
>             {
>                "name":"pytf-model"
>             }
>          ],
>          "parameters":[
>             {
>                "name":"train-epoch",
>                "type":"string"
>             }
>          ],
>          "scenarioId":"ae0bd260-41ef-4162-81b0-861bd78a8516",
>          "versionId":"0.0.1"
>       },
>       {
>          "createdAt":"2021-02-04T14:11:02+00:00",
>          "deployable":false,
>          "description":"churn and text class executable desc",
>          "id":"test-training",
>          "inputArtifacts":[
>             {
>                "name":"churn-data"
>             },
>             {
>                "name":"textclass-data"
>             }
>          ],
>          "labels":[
>             
>          ],
>          "modifiedAt":"2021-02-04T14:11:02+00:00",
>          "name":"churnntextclassexecutablename",
>          "outputArtifacts":[
>             {
>                "name":"churn-pickle"
>             },
>             {
>                "name":"pytf-model"
>             }
>          ],
>          "parameters":[
>             {
>                "name":"train-epoch",
>                "type":"string"
>             }
>          ],
>          "scenarioId":"ae0bd260-41ef-4162-81b0-861bd78a8516",
>          "versionId":"0.0.1"
>       }
>    ]
> }
> ```

> ### Note:  
> The *<modifiedAt\>* field denotes the timestamp of the latest successful sync. The output ***1970-01-01T00:00:00+00:00*** indicates an error.

<a name="task_isb_wcp_tcc"/>

<!-- task\_isb\_wcp\_tcc -->

## Get Executable Details Using Curl



<a name="task_isb_wcp_tcc__steps_jsb_wcp_tcc"/>

## Procedure

Run the following code:

```
curl --request GET "{{apiurl}}/v2/lm/scenarios/{{scenarioid}}/executables" --header "Authorization: Bearer $TOKEN" --header "ai-resource-group: $RESOURCE_GROUP" 
```



<a name="task_isb_wcp_tcc__result_bqx_ypj_wxb"/>

## Results

> ### Output Code:  
> ```json
> {
>    "createdAt":"2021-02-04T14:11:02+00:00",
>    "deployable":false,
>    "description":"churn and text class executable desc",
>    "id":"test-training",
>    "inputArtifacts":[
>       {
>          "name":"churn-data"
>       },
>       {
>          "name":"textclass-data"
>       }
>    ],
>    "labels":[
>       
>    ],
>    "modifiedAt":"2021-02-04T14:11:02+00:00",
>    "name":"churnntextclassexecutablename",
>    "outputArtifacts":[
>       {
>          "name":"churn-pickle"
>       },
>       {
>          "name":"pytf-model"
>       }
>    ],
>    "parameters":[
>       {
>          "name":"train-epoch",
>          "type":"string"
>       }
>    ],
>    "scenarioId":"ae0bd260-41ef-4162-81b0-861bd78a8516",
>    "versionId":"0.0.1"
> }
> ```

> ### Note:  
> The *<modifiedAt\>* field denotes the timestamp of the latest successful sync. The output ***1970-01-01T00:00:00+00:00*** indicates an error.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## List Executables Using Postman



<a name="task_cxf_n13_tcc__steps_b5k_xcp_tcc"/>

## Procedure

1.  Add your scenario ID as the value for the `scenarioid` environment variable.

2.  Send a GET request to the endpoint `{{apiurl}}/v2/lm/scenarios/{{scenarioid}}/executables`

3.  On the *Authorization* tab, set the type to *Bearer Token*.

4.  Set the token value to `{{token}}`.

5.  On the *Header* tab, add the following entry:


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
    
    `ai-resource-group` 
    
    </td>
    <td valign="top">
    
    *<Name of your resourceGroup\>*`default` is used\)
    
    </td>
    </tr>
    </table>
    
6.  Send the request.

    > ### Output Code:  
    > ```
    > {
    > "count": 3,
    > "resources": [
    > {
    > "createdAt": "2021-10-07T20:07:18+00:00",
    > "deployable": true,
    > "description": "Inference executable for text classification with Scikit-learn",
    > "id": "text-clf-infer-tutorial",
    > "input artifacts": [
    > ...
    > 
    > ```

    > ### Note:  
    > The *<modifiedAt\>* field denotes the timestamp of the latest successful sync. The output ***1970-01-01T00:00:00+00:00*** indicates an error.


<a name="task_h1b_wcp_tcc"/>

<!-- task\_h1b\_wcp\_tcc -->

## Get Executable Details Using Postman



<a name="task_h1b_wcp_tcc__steps_pf4_rkp_tcc"/>

## Procedure

1.  Add the environment variable `executableid` and as its value, enter the ID of the executable.

    ![](images/Add_Environment_Variable_executableid_6120596.png)

2.  Send a GET request to the endpoint `{{apiurl}}/v2/lm/scenarios/{{scenarioid}}/executables/{{executableid}}`

3.  On the *Authorization* tab, set the type to *Bearer Token*.

4.  Set the token value to `{{token}}`.

    ![](images/Bearer_Token_d6813f2.png)

5.  On the *Header* tab, add the following entry:


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
    
    `ai-resource-group` 
    
    </td>
    <td valign="top">
    
    *<Name of your resourceGroup\>* \(in the example, `default` is used\)
    
    </td>
    </tr>
    </table>
    
6.  Send the request.


