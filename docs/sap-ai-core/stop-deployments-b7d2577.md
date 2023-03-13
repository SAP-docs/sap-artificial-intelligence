<!-- loiob7d2577088c84417bbab370173d38cd8 -->

# Stop Deployments

Stopping a deployment releases the SAP AI Core runtime computing resources that it used.

A stopped deployment does not incur costs.

**Parent topic:** [Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-8deca74.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.")

[List Executables](list-executables-6af8e60.md "An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.")

[Deploy Models](deploy-models-dd16e8e.md "Utilize your model and retrieve a URL to use for inferencing.")

[Inference](inference-e348ecf.md "Use the URL from your model deployment to access the results of your model.")

[Update a Deployment](update-a-deployment-9789ddd.md "You can update a deployment with a new configuration while retaining the inference URL.")

[Delete Deployments](delete-deployments-0193d17.md#loio0193d17a7bdb4ae08a9c8301d1d8c1b8 "Deleting a deployment releases the SAP AI Core resources that it used.")

[Efficiency Features](efficiency-features-9fad26a.md "Discover features of SAP AI Core that improve model server efficiency and help manage resource consumption.")

[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs.")

 <a name="loio1fa895527bd64c6c878733e293da99dc"/>

<!-- loio1fa895527bd64c6c878733e293da99dc -->

## Stop a Single Deployment



<a name="loio1fa895527bd64c6c878733e293da99dc__section_f2y_vbd_25b"/>

## Using Postman

Stop the deployment by submitting a PATCH request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`. The header for this request is: `AI-Resource-Group: {YOUR-Resource-Group}`. The `Body` for this request is

```
{
"targetStatus": "STOPPED"
}
```

![](images/StopDeployment_f690e37.png)

Check the status of the deployment by submitting a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.



<a name="loio1fa895527bd64c6c878733e293da99dc__section_dnd_s3d_25b"/>

## Using curl

1.  Update the deployment by submitting a PATCH request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

2.  Update the request body to:

    ```
    curl --request PATCH [/pandoc/div/div/div/div/horizontalrule/orderedlist/li/codeblock/span/code
         {"filepath"}) $AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID (code] \
    --header "authorization: Bearer $TOKEN" \
    --header "ai-resource-group: $RESOURCE_GROUP" \
    --header 'content-Type: application/json' \
    --data-raw '{
    "targetStatus": "STOPPED"
    }'
    
    ```

    > ### Output Code:  
    > ```
    > {
    >     "id": "d748fdae9f88a9b0",
    >     "message": "Deployment modification scheduled"
    > }
    > 
    > ```

3.  Check the status of the deployment by submitting a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

    ```
    curl --request GET [/pandoc/div/div/div/div/horizontalrule/orderedlist/li/codeblock/span/code
         {"filepath"}) $AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID (code] \ --header "Authorization: Bearer $TOKEN" \ --header "ai-resource-group: $RESOURCE_GROUP"
    ```


 <a name="loio331cdf505d1c47618256a83920dd7c9a"/>

<!-- loio331cdf505d1c47618256a83920dd7c9a -->

## Stop Multiple Deployments



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




<a name="loio331cdf505d1c47618256a83920dd7c9a__section_sfh_r2m_jwb"/>

## Using curl

Update the request body to:

```
curl --request PATCH [/pandoc/div/div/div/div/horizontalrule/codeblock/span/code
     {"filepath"})  - /deployments (code] \
    --header {"deployments": [
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
>   "deployments": [
>     {
>       "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "message": "Deployment modification scheduled"
>     },
>     {
> 
>       "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
>       "message": "Deployment modification scheduled"
>     }
>   ]
> }
> 
> ```



<a name="loio331cdf505d1c47618256a83920dd7c9a__section_f51_13m_jwb"/>

## Using Postman

Send a bulk PATCH request to: `- /deployments`

```
{
"deployments": [
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
}'

```

> ### Output Code:  
> ```
> {
>   "deployments": [
>     {
>       "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "message": "Deployment modification scheduled"
>     },
>     {
> 
>       "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
>       "message": "Deployment modification scheduled"
>     }
>   ]
> }
> 
> ```

**Related Information**  


[About the AI API](about-the-ai-api-716d4c3.md "The AI API lets you manage your AI assets (such as training scripts, data, models, and model servers) across multiple runtimes.")

