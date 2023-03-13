<!-- loio9fad26a7e6894e3cbd80da723ce466fc -->

# Efficiency Features

Discover features of SAP AI Core that improve model server efficiency and help manage resource consumption.



<a name="loio9fad26a7e6894e3cbd80da723ce466fc__section_xqk_dfs_xvb"/>

## Autoscaling

SAP AI Core includes parameters to reduce the number of nodes used based on current consumption, or impose usage limits during periods of high consumption. For more information, see [Serving Templates](serving-templates-20a8667.md).



<a name="loio9fad26a7e6894e3cbd80da723ce466fc__section_bny_gfs_xvb"/>

## Global Node Pool

When the inference server scales up from a stopped state, there is some additional response time. To reduce this, SAP AI Core has a Global Node Pool. Commonly used nodes are reserved to allow for shorter response times. To reduce response times further, avoid a cold start altogether by setting your autoscaling parameter to `1`. For more information, see [Serving Templates](serving-templates-20a8667.md).



<a name="loio9fad26a7e6894e3cbd80da723ce466fc__section_pjn_hfs_xvb"/>

## TTL

The default duration is indefinite, however the `ttl` parameter limits the duration of a deployment to minutes, hours, or days. For more information, see [Deploy Models](deploy-models-dd16e8e.md) and [About the AI API](about-the-ai-api-716d4c3.md).

**Parent topic:** [Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-8deca74.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.")

[List Executables](list-executables-6af8e60.md "An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.")

[Deploy Models](deploy-models-dd16e8e.md "Utilize your model and retrieve a URL to use for inferencing.")

[Inference](inference-e348ecf.md "Use the URL from your model deployment to access the results of your model.")

[Update a Deployment](update-a-deployment-9789ddd.md "You can update a deployment with a new configuration while retaining the inference URL.")

[Stop Deployments](stop-deployments-b7d2577.md#loiob7d2577088c84417bbab370173d38cd8 "Stopping a deployment releases the SAP AI Core runtime computing resources that it used.")

[Delete Deployments](delete-deployments-0193d17.md#loio0193d17a7bdb4ae08a9c8301d1d8c1b8 "Deleting a deployment releases the SAP AI Core resources that it used.")

[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs.")

