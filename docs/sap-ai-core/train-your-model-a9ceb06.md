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

-   Dedicated object store buckets used as data storage. A default bucket is provided per resource group.

-   Bring your own hyperscaler-backed object store buckets.


The execution engine in SAP AI Core leverages the [Argo Workflows](https://argoproj.github.io/workflows) open source project. It supports container-native workflows and pipelines modeled as direct acyclic graphs or steps. The Argo Workflows are used to ingest data, perform preprocessing and postprocessing, and train models and execute batch inference pipelines. SAP AI Core also leverages the parallel processing of steps in the form of a [DAG \( Directed Acyclic Graph\) structure](https://argoproj.github.io/argo-workflows/workflow-concepts/#dag) in workflow templates. For information about how using parallel nodes may affect your costs, see [Metering and Pricing](metering-and-pricing-b5c7215.md).

It is possible to train the same model multiple times, with varying parameters \(for parameters compatible with the workflow, only\) and evaluate them in SAP AI Launchpad.

-   **[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure
		resources for
		different
		tasks, based on demand.
		SAP AI Core provides several preconfigured infrastructure bundles called
			“resource plans” for this purpose.")**  
You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.
-   **[Workflow Templates](workflow-templates-83523ab.md " Here, you can find a minimal workflow example template, that can be adapted to meet
    the requirements of your workflow. ")**  
 Here, you can find a minimal workflow example template, that can be adapted to meet the requirements of your workflow.
-   **[List Scenarios](list-scenarios-deedde5.md "")**  

-   **[List Executables](list-executables-80895a4.md "")**  

-   **[Create Configurations](create-configurations-884ae34.md "")**  

-   **[List Configurations](list-configurations-8074b2a.md "")**  

-   **[Start Training](start-training-54b44e4.md "")**  

-   **[Stop Training Instances](stop-training-instances-3d85344.md "")**  

-   **[Delete Training Instances](delete-training-instances-612ce17.md "")**  

-   **[Efficiency Features](efficiency-features-4cb76f7.md "Discover features of the SAP AI Core runtime that improve
		efficiency and help manage resource consumption.")**  
Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.
-   **[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs. ")**  
Information about API processing and metrics, are stored and accessed in the deployment and execution logs.
-   **[Training Schedules](training-schedules-2b702f8.md "")**  


**Parent topic:** [ML Operations](ml-operations-7f5aa9b.md "This section guides you through the end-to-end AI lifecycle of SAP AI Core.")

**Related Information**  


[Connect Your Data](connect-your-data-9508bdb.md "Use cloud storage with SAP AI Core to store AI assets such as datasets and model files. You use Artifacts in SAP AI Core to reference to your AI Assets.")

[Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

