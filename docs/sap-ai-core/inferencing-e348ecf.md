<!-- loioe348ecfd5b334423aaae6da3d8307a92 -->

# Inferencing

Use the URL from your model deployment to access the results of your model.

To inference your model, send a POST request to <code>"$DEPLOYMENT_URL/<i class="varname">&lt;path that you have defined&gt;</i>"</code> For example, TensorFlow models follow the path `v1/models/$MODEL_NAME:predict`.

**Parent topic:**[Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

**Related Information**  


[Choose an Instance](choose-an-instance-abd672f.md "You can configure SAP AI Core to use different infrastructure instances for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” and “instance types” for this purpose.")

[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.")

[List Executables](list-executables-6af8e60.md "An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts (datasets or models) and parameters (custom key-pair values) that enable the template to be reused in different scenarios.. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.")

[Deploy Models](deploy-models-dd16e8e.md "")

[Update a Deployment](update-a-deployment-9789ddd.md "")

[Stop Deployments](stop-deployments-b7d2577.md " ")

[Delete Deployments](delete-deployments-0193d17.md " ")

[Efficiency Features](efficiency-features-9fad26a.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "Deployment and execution logs contain information about API processing and metrics.")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__prereq_h2z_p2b_wxbg"/>

## Prerequisites

-   The deployment must have the state “pending”, “running” or “dead”.

-   The new configuration contains the same `scenarioId` and `executableId` as the currently active configuration.


> ### Note:  
> Dead deployments can only be patched within 7 days. After 7 days from the time that the deployment reached DEAD status, it will be deleted and will no longer be available.



<a name="task_i3h_n13_tcc__context_zxg_jdb_twxb"/>

## Context

Use the URL from your model deployment to access the results of your model.

To inference your model, send a POST request to `{{apiurl}}/v2/lm/deployments` For example, TensorFlow models follow the path `v1/models/MODEL_NAME:predict`.



<a name="task_i3h_n13_tcc__steps_qqg_fth_vcc"/>

## Procedure

In this example, the name of the model is “churn”.

```
curl --location --request POST ' $deploymentUrl/v1/models/churn:predict' \
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__prereq_h2z_p2b_wxdb"/>

## Prerequisites

-   The deployment must have the state “pending”, “running” or “dead”.

-   The new configuration contains the same `scenarioId` and `executableId` as the currently active configuration.


> ### Note:  
> Dead deployments can only be patched within 7 days. After 7 days from the time that the deployment reached DEAD status, it will be deleted and will no longer be available.



<a name="task_cxf_n13_tcc__context_zxg_jdb_wxb"/>

## Context

Use the URL from your model deployment to access the results of your model.

To inference your model, send a POST request to `{{apiurl}}/v2/lm/deployments` For example, TensorFlow models follow the path `v1/models/MODEL_NAME:predict`.



<a name="task_cxf_n13_tcc__steps_d2x_dth_vcc"/>

## Procedure

As the deployment URL, pass the URL that was returned in the response body in the `{{apiurl}}/v2/lm/deployments` call \(see [Deploy Models](deploy-models-dd16e8e.md)\).

As the request body, enter a sample instance in JSON format.

In this example, the name of the model is “churn”.

```
POST {{deploymenturl}}/v1/models/churn:predict
```

```
{
"region": 3,
"tenure": 37,
"age": 53,
"address": 13,
"income": 48,
"employ": 10,
"gender": 0,
"equip": 0,
...
```

