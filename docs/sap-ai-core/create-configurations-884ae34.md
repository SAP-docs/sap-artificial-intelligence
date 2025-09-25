<!-- loio884ae340eb4a409b9548aee135e98b3f -->

# Create Configurations

A configuration is a collection of parameters, artifact references \(such as datasets or models\), and environment settings that are used to instantiate and run an execution or deployment of an executable or template.

**Parent topic:**[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Workflow Templates](workflow-templates-83523ab.md "Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.")

[List Scenarios](list-scenarios-deedde5.md "A scenario is an implementation of a specific AI use case within a user's tenant. It consists of a pre-defined set of AI capabilities in the form of executables and templates.")

[List Executables](list-executables-80895a4.md "An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts (datasets or models) and parameters (custom key-pair values) that enable the template to be reused in different scenarios.")

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

## Using Curl



<a name="task_i3h_n13_tcc__steps_o2h_3bq_tcc"/>

## Procedure

Run the following code:

```
curl --request POST "$AI_API_URL/v2/lm/configurations" --header "Authorization: Bearer $TOKEN" --header "AI-Resource-Group: $RESOURCE_GROUP" --header "Content-Type: application/json" \
-d '{ 
    "name": "dummy-configuration", 
    "executableId": "'"$EXECUTABLE"'", 
    "scenarioId": "'"$SCENARIO"'", 
    "parameterBindings": [ 
      { 
        "key": "parameter_name_in_template", 
        "value": "some_value" 
      } 
    ], 
    "inputArtifactBindings": [ 
      { 
        "key": "input_artifact_name_in_template", 
        "artifactId": "a4d62a76-52aa-44cf-a789-743246d6d55b" 
      } 
    ] 
  }' 
```

> ### Output Code:  
> ```json
> {
>    "id":"f5bf305f-7c3f-4882-9f6b-8b95e3687b9b",
>    "message":"Configuration created"
> }
> ```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_ysp_kbp_yxb"/>

## Procedure

1.  Send a POST request to the endpoint `{{apiurl}}/v2/lm/configurations`

2.  On the *Authorization* tab, set the type to *Bearer Token*.

3.  Set the token value to `{{token}}`.

4.  On the *Header* tab, add the following entries:


    <table>
    <tr>
    <th valign="top">

    KEY
    
    </th>
    <th valign="top">

    VALUE
    
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
    <tr>
    <td valign="top">
    
    `Content-Type` 
    
    </td>
    <td valign="top">
    
    `application/json` 
    
    </td>
    </tr>
    </table>
    
5.  On the *Body* tab, select the *raw* radio button and add the request body as given below:

    ```
    {
        "name": "configuration-name",
        "executableId": "<executable ID>",
        "scenarioId": "<scenario ID>",
        "parameterBindings": [
          {
            "key": "<parameter name>",
            "value": "<value>"
          }
        ],
        "inputArtifactBindings": [
          {
            "key": "<artifact name>",
            "artifactId": "<artifact ID>"
          }
        ]
      }
    
    ```

    > ### Output Code:  
    > ```
    > ...
    > "": [
    > {
    > "key": "churn-data",
    > "artifactId": "896e9230-9219-47fa-89c7-c47db7d45d6a"
    > }
    > ]
    > ```

6.  Send the request.


