<!-- loioe348ecfd5b334423aaae6da3d8307a92 -->

# Inferencing

Use the URL from your model deployment to access the results of your model.

To inference your model, send a POST request to <code>"$DEPLOYMENT_URL/<i class="varname">&lt;path that you have defined&gt;</i>"</code> For example, TensorFlow models follow the path `v1/models/$MODEL_NAME:predict`.



<a name="loioe348ecfd5b334423aaae6da3d8307a92__section_q1c_k2q_brb"/>

## Inference with Postman

As the deployment URL, pass the URL that was returned in the response body in the `{{apiurl}}/v2/lm/deployments` call \(see [Deploy Models](deploy-models-dd16e8e.md)\).

As the request body, enter a sample instance in JSON format.

![](images/Inference_a8693ed.png)



<a name="loioe348ecfd5b334423aaae6da3d8307a92__section_czw_k2q_brb"/>

## Inference with curl

In this example, the name of the model is “churn”.

```
curl --location --request POST '$AI_API_URL/v1/models/churn:predict' \
```

**Parent topic:** [Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-8deca74.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.")

[List Executables](list-executables-6af8e60.md "An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.")

[Deploy Models](deploy-models-dd16e8e.md "")

[Update a Deployment](update-a-deployment-9789ddd.md "")

[Stop Deployments](stop-deployments-b7d2577.md " ")

[Delete Deployments](delete-deployments-0193d17.md " ")

[Efficiency Features](efficiency-features-9fad26a.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs.")

