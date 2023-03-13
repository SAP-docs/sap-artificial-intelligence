<!-- loio3d853443027449d9a33723165b19b25a -->

# Stop Training Instances

You can stop a running execution by submitting a PATCH request to `$AI_API_URL/v2/lm/executions/$EXECUTION \`.

> ### Note:  
> Stop is only disabled if the status is running or pending.

**Parent topic:** [Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Workflow Templates](workflow-templates-83523ab.md "Here, you can find a minimal workflow example template, that can be adapted to meet the requirements of your workflow.")

[List Scenarios](list-scenarios-deedde5.md "A scenario is a group of related executables for a use case within the user's tenant. A scenario can have multiple versions that further correspond to the different versions of executables.")

[List Executables](list-executables-80895a4.md "An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a scenario and get details of specific executables from a scenario. Workflow templates are mapped to training executables.")

[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references, and executables that are used to run an execution or deployment.")

[List Configurations](list-configurations-8074b2a.md "")

[Start Training](start-training-54b44e4.md "Start training and check the status of the execution.")

[Delete Training Instances](delete-training-instances-612ce17.md#loio612ce172e609432a840a22eb211ecf7b "Deleting a training instance releases the SAP AI Core resources that it used.")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs.")

[Training Schedules](training-schedules-2b702f8.md "")

 <a name="loio07870dfc89fe4218baeda95e994936da"/>

<!-- loio07870dfc89fe4218baeda95e994936da -->

## Stop a Single Training Instance



<a name="loio07870dfc89fe4218baeda95e994936da__section_ypf_lgp_brb"/>

## Using Postman

![](images/Aborting_an_Execution_with_Postman_3e10c1e.png)



<a name="loio07870dfc89fe4218baeda95e994936da__section_imm_lgp_brb"/>

## Using curl

```
curl --request PATCH [/pandoc/div/div/div/div/horizontalrule/codeblock/span/code
     {"filepath"}) $AI_API_URL/v2/lm/executions/$EXECUTION \ (code] --header "Authorization: Bearer $TOKEN" --header "ai-resource-group: $RESOURCE_GROUP" --header "Content-Type: application/json"
-d '{
    "targetStatus": "STOPPED"
}'

```

> ### Output Code:  
> ```json
> {
>     "id": "ee6769e4dc19c0fd",
>     "message": "Execution modification scheduled"
> }
> 
> ```

 <a name="loio09b4810ad29445d19025836ed1ac5151"/>

<!-- loio09b4810ad29445d19025836ed1ac5151 -->

## Stop Multiple Training Instances



`bulkUpdates` is a meta capability endpoint of the AI API. It enables or disables bulk PATCH operations. For more information, see [About the AI API](about-the-ai-api-716d4c3.md).

The feature is set to false by default. To enable bulk PATCH operations, your template must contain the following snippet, with the relevant values set to `true`.

```

Meta:
  "bulkUpdates": {
        "executions": false,
        "deployments": false
      }
```

About `bulkUpdates`:

-   The maximum number of updates per request is 100.

-   Your bulk update can contain a mixture of STOP and DELETE requests.

-   An ID can only appear once per bulk request. For multiple modifications of the same ID, multiple requests are needed.

-   Only *stopped*, *dead* or *unknown* executions or deployments can be deleted.

-   Only *running* or *pending* executions or deployments can be stopped.




<a name="loio09b4810ad29445d19025836ed1ac5151__section_tfh_r2m_jwb"/>

## Using Postman

Send a bulk PATCH request to: `- /executions`

Update the request body to:

```
{
  "executions": [
    {
      "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
      "targetStatus": "STOPPED"
    },
    {

      "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
      "targetStatus": "DELETED"
    }
  ]
}

```

> ### Output Code:  
> ```
> {
>   "executions": [
>     {
>       "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "message": "Execution modification scheduled"
>     },
>     {
> 
>       "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
>       "message": "Execution modification scheduled"
>     }
>   ]
> }
> 
> ```



<a name="loio09b4810ad29445d19025836ed1ac5151__section_sfh_r2m_jwb"/>

## Using curl

Update the request body to:

```
curl --request PATCH [/pandoc/div/div/div/div/horizontalrule/codeblock/span/code
     {"filepath"})  - /executions (code] \
    --header {"executions": [
    {
      "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
      "targetStatus": "STOPPED"
    },
    {
      "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
      "targetStatus": "DELETED"
    }
  ]
}

```

> ### Output Code:  
> ```
> {
>   "executions": [
>     {
>       "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "message": "Execution modification scheduled"
>     },
>     {
> 
>       "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
>       "message": "Execution modification scheduled"
>     }
>   ]
> }
> 
> ```

**Related Information**  


[About the AI API](about-the-ai-api-716d4c3.md "The AI API lets you manage your AI assets (such as training scripts, data, models, and model servers) across multiple runtimes.")
