<!-- loio7f93e8f3f385454e9a69178183a8ecc5 -->

# Use Your Model

You deploy your AI learning model to run inferences against it.

SAP AI Core provides the means to run AI training and offline batch inference jobs, using the required computational resources \(such as GPUs\) efficiently.

You can use a model trained in SAP AI Core, or your own pretrained model for deployment and inferencing.

The model serving service includes:

-   Serving of AI models through fast, secure, and resource-efficient inference endpoints that can be integrated into online inference scenarios.

-   Flexibility to deploy user-supplied Docker images.

-   Cost-efficient serving \(for example, by autoscaling or serverless support or multimodel serving\).

-   Parameterized serving templates for main tenants to manage their serving instances.

-   Serving instances in resource group namespaces with specific parameters and resource isolation.


The serving templates are used to create model servers. When a model server is up and running, it processes incoming inference requests and returns the results from the AI learning model. Serving templates define how a model is to be deployed. For the model to work, you must provide a `spec` in line with the [Serving Templates](serving-templates-20a8667.md), together with input parameters and artifacts.

Restrict the number of nodes used for processing by specifying parameters minReplicas and maxReplicas.

-   **[Choose an Instance](choose-an-instance-abd672f.md "You can configure SAP AI Core to use different infrastructure
		instances for different tasks, based on demand. SAP AI Core provides
		several preconfigured infrastructure bundles called “resource plans” and “instance types” for this purpose.")**  
You can configure SAP AI Core to use different infrastructure instances for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” and “instance types” for this purpose.
-   **[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main
    tenant. Serving templates define how a model is to be deployed.")**  
You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.
-   **[List Executables](list-executables-6af8e60.md "An executable is a reusable template that defines a workflow or pipeline for tasks
      such as training a machine learning model or creating a deployment. It contains placeholders
      for input artifacts (datasets or models) and parameters (custom key-pair values) that enable
      the template to be reused in different scenarios.. You can list all of the executables in a
      resource group and get details of specific executables from a resource group. Serving
      templates are mapped to deployment executables.")**  
An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts \(datasets or models\) and parameters \(custom key-pair values\) that enable the template to be reused in different scenarios.. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.
-   **[Deploy Models](deploy-models-dd16e8e.md "")**  

-   **[Inferencing](inferencing-e348ecf.md "")**  

-   **[Update a Deployment](update-a-deployment-9789ddd.md "")**  

-   **[Stop Deployments](stop-deployments-b7d2577.md " ")**  

-   **[Delete Deployments](delete-deployments-0193d17.md " ")**  

-   **[Efficiency Features](efficiency-features-9fad26a.md "Discover features of the SAP AI Core runtime that improve efficiency
		and help manage resource consumption.")**  
Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.
-   **[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "Deployment and execution logs contain information about API
            processing and metrics.")**  
Deployment and execution logs contain information about API processing and metrics.

**Parent topic:**[ML Operations](ml-operations-7f5aa9b.md "This section guides you through the end-to-end AI lifecycle of SAP AI Core.")

**Related Information**  


[Connect Your Data](connect-your-data-9508bdb.md "Use cloud storage with SAP AI Core to store AI assets such as datasets and model files. You use Artifacts in SAP AI Core to reference to your AI Assets.")

[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

