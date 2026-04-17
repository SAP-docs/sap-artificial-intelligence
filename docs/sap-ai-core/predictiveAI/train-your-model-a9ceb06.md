<!-- loioa9ceb06ba9b146d0b2c410cbd685ead6 -->

# Train Your Model

You execute a training workflow to train your AI learning model.

SAP AI Core uses data as specified by your resource group. Models are specified in your workflow and are trained on a remote server. The resulting artifacts are stored to your object store.

The execution service includes:

-   Batch jobs/pipelines via a state-of-the-art workflow engine.

-   Parameterized templates for pipelines stored and managed at tenant level.

-   Pipeline instances with specific parameters and resource isolation.

-   Support for bringing own Docker registries and Docker images for running pipeline steps.

-   Data extraction and validation modeled as pipeline steps.

-   Bring your own hyperscaler-backed object store buckets.

-   Dedicated object store buckets used as data storage. A **default** bucket should be provided by users per resource group.


> ### Restriction:  
> You must create an **object store secret** named **default** to store the training output artifact \(for example, a model\). If this default object store secret is missing, the training pipeline fails.
> 
> For **input training artifacts only**, you can create multiple object store secrets with different names as needed.
> 
> All artifacts are required to have a name. Templates that include artifacts without names return an error.
> 
> For more information, see [Register an Object Store Secret](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/b083d73f672c428faac3048b74733546.html "Connect SAP AI Core to a cloud object store and manage access using an object store secret. The connected storage stores your dataset, models, and other cache files of the Metaflow Library for SAP AI Core.") :arrow_upper_right:.

The execution engine in SAP AI Core leverages the [Argo Workflows](https://argoproj.github.io/workflows/) open source project. It supports container-native workflows and pipelines modeled as direct acyclic graphs or steps. The Argo Workflows are used to ingest data, perform preprocessing and postprocessing, and train models and execute batch inference pipelines. SAP AI Core also leverages the parallel processing of steps in the form of a [DAG \( Directed Acyclic Graph\) structure](https://argoproj.github.io/argo-workflows/workflow-concepts/#dag) in workflow templates. For information about how using parallel nodes may affect your costs, see [Metering and Pricing for SAP AI Core](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/1e6cbac9c2cb4dcba7929035982a7e7b.html "SAP AI Core provides a scalable infrastructure for AI model management, with usage-based pricing that lets you pay only for the resources you use.") :arrow_upper_right:.

> ### Note:  
> Argo Workflow isn’t optimized for time critical tasks. Each step must be scheduled onto a node in the cluster, and the cluster initialized. The time this takes depends on the load of the workflow controller and the node availability in the cluster. Therefore, it isn’t recommended to use multistep Argo Workflows for time-critical tasks.

It’s possible to train the same model multiple times, with varying parameters \(for parameters compatible with the workflow, only\) and evaluate them in SAP AI Launchpad.

-   **[Choose an Instance](choose-an-instance-57f4f19.md "You can configure SAP AI Core to use different infrastructure
		instances for different tasks, based on demand. SAP AI Core provides
		several preconfigured infrastructure bundles called “instance types” and “resource plans” for this purpose.")**  
You can configure SAP AI Core to use different infrastructure instances for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “instance types” and “resource plans” for this purpose.
-   **[Workflow Templates](workflow-templates-83523ab.md " Here, you'll find a basic workflow example template. Feel free to adjust it to suit
    your workflow needs.")**  
 Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.
-   **[List Scenarios](list-scenarios-deedde5.md "A scenario is an implementation of a specific AI use case within a user's tenant. It
		consists of a pre-defined set of AI capabilities in the form of executables and
		templates.")**  
A scenario is an implementation of a specific AI use case within a user's tenant. It consists of a pre-defined set of AI capabilities in the form of executables and templates.
-   **[List Executables](list-executables-80895a4.md "An executable is a reusable template that defines a workflow or pipeline for tasks
      such as training a machine learning model or creating a deployment. It contains placeholders
      for input artifacts (datasets or models) and parameters (custom key-pair values) that enable
      the template to be reused in different scenarios.")**  
An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts \(datasets or models\) and parameters \(custom key-pair values\) that enable the template to be reused in different scenarios.
-   **[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references (such as datasets or
    models), and environment settings that are used to instantiate and run an execution or
    deployment of an executable or template.")**  
A configuration is a collection of parameters, artifact references \(such as datasets or models\), and environment settings that are used to instantiate and run an execution or deployment of an executable or template.
-   **[List Configurations](list-configurations-8074b2a.md "")**  

-   **[Using Artifact Signatures](using-artifact-signatures-2f02a1d.md "Artifact signatures in the form of a hash can be added to output artifacts from executions.")**  
Artifact signatures in the form of a hash can be added to output artifacts from executions.
-   **[Start Training](start-training-54b44e4.md "")**  

-   **[Delete a Single Training Instance](delete-a-single-training-instance-dd71f16.md "")**  

-   **[Stop a Single Training Instance](stop-a-single-training-instance-07870df.md "")**  

-   **[Efficiency Features](efficiency-features-4cb76f7.md "Discover features of the SAP AI Core runtime that improve
		efficiency and help manage resource consumption.")**  
Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.
-   **[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "Deployment and execution logs contain information about API
            processing and metrics.")**  
Deployment and execution logs contain information about API processing and metrics.
-   **[Training Schedules](training-schedules-2b702f8.md "")**  


