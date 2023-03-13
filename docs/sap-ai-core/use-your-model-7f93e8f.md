<!-- loio7f93e8f3f385454e9a69178183a8ecc5 -->

# Use Your Model

You deploy your AI learning model to run inferences against it.

SAP AI Core provides the means to run AI training and offline batch inference jobs, using the required computational resources \(such as GPUs\) efficiently.

You can use a model trained in SAP AI Core, or your own pretrained model for deployment and inferencing.

The model serving service includes:

-   Serving of AI models through fast, secure, and resource-efficient inference endpoints that can be integrated into online inference scenarios.

-   Flexibility to deploy user-supplied Docker images.

-   Cost-efficient serving \(for example, by autoscaling/serverless support or multimodel serving\).

-   Parameterized serving templates for main tenants to manage their serving instances.

-   Serving instances in resource group namespaces with specific parameters and resource isolation.


The serving templates are used to create model servers. When a model server is up and running, it processes incoming inference requests and returns the results from the AI learning model. Serving templates define how a model is to be deployed. For the model to work, you must provide a `spec` in line with the [Serving Template API Reference](serving-template-api-reference-51b2271.md), together with input parameters and artifacts.

Restrict the number of nodes used for processing by specifying parameters minReplicas and maxReplicas.

-   **[Choose a Resource Plan](choose-a-resource-plan-8deca74.md "You can configure SAP AI Core to use different infrastructure
		resources for
		different
		tasks, based on task demand.
		SAP AI Core provides several preconfigured infrastructure bundles called
			“resource plans” for this purpose. ")**  
You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.
-   **[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main
    tenant. Serving templates define how a model is to be deployed.")**  
You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.
-   **[List Executables](list-executables-6af8e60.md "An executable is a
                                    template that is instantiated for a purpose, such as training a
                                    model or creating a deployment. You can list all of the executables in a resource group and get
      details of specific executables from a resource group. Serving templates are mapped to deployment executables.")**  
An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.
-   **[Deploy Models](deploy-models-dd16e8e.md "Utilize your model and retrieve a URL to use for inferencing.")**  
Utilize your model and retrieve a URL to use for inferencing.
-   **[Inference](inference-e348ecf.md "Use the URL from your model deployment to access the results of your model.")**  
Use the URL from your model deployment to access the results of your model.
-   **[Update a Deployment](update-a-deployment-9789ddd.md "You can update a deployment with a new configuration while retaining the inference
		URL.")**  
You can update a deployment with a new configuration while retaining the inference URL.
-   **[Stop Deployments](stop-deployments-b7d2577.md#loiob7d2577088c84417bbab370173d38cd8 "Stopping a deployment releases the SAP AI Core runtime computing
		resources that it used. ")**  
Stopping a deployment releases the SAP AI Core runtime computing resources that it used.
-   **[Delete Deployments](delete-deployments-0193d17.md#loio0193d17a7bdb4ae08a9c8301d1d8c1b8 "Deleting a deployment releases the SAP AI Core resources that it
		used. ")**  
Deleting a deployment releases the SAP AI Core resources that it used.
-   **[Efficiency Features](efficiency-features-9fad26a.md "Discover features of SAP AI Core that improve model server
		efficiency and help manage resource consumption.")**  
Discover features of SAP AI Core that improve model server efficiency and help manage resource consumption.
-   **[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs. ")**  
Information about API processing and metrics, are stored and accessed in the deployment and execution logs.

**Parent topic:** [ML Operations](ml-operations-7f5aa9b.md "This section guides you through the end-to-end AI lifecycle of SAP AI Core.")

**Related Information**  


[Administration](administration-7937fc1.md "Creating secrets for your tools, means that you can connect external programs and tools without compromising your account. The tools can be used to incorporate version control, cloud storage and portable containers.")

[Connect Your Data](connect-your-data-9508bdb.md "Use cloud storage with SAP AI Core to store AI assets such as datasets and model files. You use Artifacts in SAP AI Core to reference to your AI Assets.")

[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

[Metrics](metrics-36f8bec.md "The AI API provides the ability to track metrics, and to customize or filter which metrics are reported.")

