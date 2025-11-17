<!-- loiodd16e8ef75654dde831e7b812688e4fa -->

# Deploy Models

**Parent topic:**[Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

**Related Information**  


[Choose an Instance](choose-an-instance-abd672f.md "You can configure SAP AI Core to use different infrastructure instances for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” and “instance types” for this purpose.")

[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.")

[List Executables](list-executables-6af8e60.md "An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts (datasets or models) and parameters (custom key-pair values) that enable the template to be reused in different scenarios.. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.")

[Inferencing](inferencing-e348ecf.md "")

[Update a Deployment](update-a-deployment-9789ddd.md "")

[Stop Deployments](stop-deployments-b7d2577.md " ")

[Delete Deployments](delete-deployments-0193d17.md " ")

[Efficiency Features](efficiency-features-9fad26a.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "Deployment and execution logs contain information about API processing and metrics.")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_klv_x3h_vcc"/>

## Procedure

1.  Trigger the deployment.

    ```
    curl --request POST $AI_API_URL/v2/lm/deployments \
        --header "Authorization: Bearer $TOKEN" \
        --header "AI-Resource-Group: $RESOURCE_GROUP"
        --data-raw '{
            "configurationId": " 2b72d740-5a89-4cf7-b37c-85973eeed6ae "
        }'
    
    ```

    > ### Output Code:  
    > ```json
    > {
    >   "deploymentUrl": "",
    >   "id": "dda5d19065d5b1f4",
    >   "message": "Deployment created.",
    >   "status": "UNKNOWN"
    > }
    > ```

2.  Note the deploy environment variable for later use.

3.  Check the status of the deployment.

    ```
    curl --request GET $AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID \
        --header "Authorization: Bearer $TOKEN" \
        --header "AI-Resource-Group: $RESOURCE_GROUP"   
    ```

    > ### Note:  
    > Configurations are checked when POST requests are submitted. If a configuration is incorrect configuration, an error message outlining the details will be returned..
    > 
    > If the status of the deployment is dead or pending after successful submission, there might be errors in the deployment. You can check the deployment logs for more details, see [Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md).

    > ### Output Code:  
    > ```json
    > {
    >   "configurationExecutableId": "hello-tf-1-15",
    >   "configurationId": "2b72d740-5a89-4cf7-b37c-85973eeed6ae",
    >   "configurationName": "hello-tf-1-15-config",
    >   "createdAt": "2020-11-11T06:34:24Z",
    >   "createdBy": "user",
    >   "deploymentUrl": "https://my-deployment-url.com",
    >   "id": "d291766fd1072b3f",
    >   "modifiedAt": "2020-11-11T06:37:29Z",
    >   "modifiedBy": "user",
    >   "scenarioId": "dba85cf3-2d69-498d-8ce5-4a415c9116dc",
    >   "status": "RUNNING",
    >   "targetStatus": "RUNNING",
    >   "versionId": "0.1.0"
    > }
    > ```


<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_zkd_whh_vcc"/>

## Procedure

1.  Send a POST request to the endpoint `{{apiurl}}/v2/lm/deployments`.

2.  Pass the `configurationId` in the request body.

    ```
    {
    "deploymentUrl": "",
    "id": "d94771b082c5cbcc",
    "message": "Deployment scheduled.",
    "status": "UNKNOWN"
    }
    ```

3.  Check the status of the deployment by sending a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

    ```
    {
    "deploymentUrl": "your deployment url",
    "modifiedAt": "2021-09-27T10:48:51Z",
    "scenarioId": "b5379278-887c-4156-9a65-a6c11d6f1a71",
    "startTime": "2021-09-27T10:33:12Z",
    "status": "RUNNING"
    }
    ```

    > ### Note:  
    > Configurations are checked when POST requests are submitted. If a configuration is incorrect configuration, an error message outlining the details will be returned..
    > 
    > If the status of the deployment is dead or pending after successful submission, there might be errors in the deployment. You can check the deployment logs for more details, see [Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md).


<a name="concept_z3s_f3h_vcc"/>

<!-- concept\_z3s\_f3h\_vcc -->

## Parameters and Quotas



<a name="concept_z3s_f3h_vcc__d121e1165"/>

## Optional Parameters

The duration of a deployment can be limited using the `ttl` parameter. It takes an integer for quantity, and a single letter to specify units of time. Only minutes \(`m`\), hours \(`h`\) and days \(`d`\), are supported, and values must be natural numbers. For example, `"ttl": "5h"` gives the deployment a duration of 5 hours. `4.5h` and `4h30m` are not valid inputs. If no value is passed, the duration of the deployment if indefinite. Once the duration expires, the deployment is stopped and deleted.



<a name="concept_z3s_f3h_vcc__d121e1196"/>

## Deployment Quotas

Each tenant is assigned a default quota that limits the number of deployments and replicas per deployment. If you reach this quota, your deployment will not be created, and you will be notified. You can free up your quota by deleting existing deployments.

Alternatively, you can request a quota increase by creating a ticket. The `component` name is `CA-ML-AIC` and ticket title is `Request to Increase Quota`.

