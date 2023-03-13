<!-- loioaba87973dcba44389fe7479451cf0d6a -->

# Models

A model is a type of artifact that results from a training process.

Models are stored as files in your connected hyperscaler object storage. The object storage is associated with your AI runtime connection.

 SAP AI Launchpad can be used with multiple hyperscaler object stores, such as Amazon S3, OSS, and WebHDFS.

Models are unique to a resource group.

You can create a model, by running an execution in the *ML Operations* app. Models which are created this way, also include details of the source execution. Alternatively, you can reference an existing model by registering it for use.

**About Model Registration**

-   Model creation: A model is created as the output of an execution within the *ML Operations* app. Models which result from this training process are **automatically** stored as files in your object store, and are automatically registered as model artifacts. Each model is assigned a unique model ID.

-   Model registration: A model is manually registered using SAP AI Launchpad \(see [Register a Model](register-a-model-8162c5d.md)\). Registering a model enables you to reference an existing model which is stored in hyperscaler data storage. After you register a model, you'll see it listed with all other models in the app. You register a model using the *ML Operations* app.

-   Model registration: A model is manually registered using SAP AI Core \(see [Create Artifacts](https://help.sap.com/docs/AI_CORE/808d9d442fb0484e9b818924feeb9add/CLOUD/66413f1d9fbf4758a0d739eaf1c95dc7.html)\).


-   **[Investigate a Model](investigate-a-model-90d641f.md "Use the ML
                                    Operations app to list the models for your
		selected connection, and investigate their origin.")**  
Use the *ML Operations* app to list the models for your selected connection, and investigate their origin.
-   **[Register a Model](register-a-model-8162c5d.md "Use the ML
                                    Operations app to manually register a model that
		is stored in your object store.")**  
Use the *ML Operations* app to manually register a model that is stored in your object store.
-   **[View Metrics for a Model](view-metrics-for-a-model-354931f.md "The Metrics tab provides an overview of the quality of a model.
		The metric data is logged by a workflow executable  during an execution (training
		process).")**  
The *Metrics* tab provides an overview of the quality of a model. The metric data is logged by a workflow executable during an execution \(training process\).
-   **[Compare Models](compare-models-60fd898.md "You can compare models to determine which configuration parameters result in optimum
		results. ")**  
You can compare models to determine which configuration parameters result in optimum results.

**Related Information**  


[Artifact Management](https://help.sap.com/docs/AI_CORE/808d9d442fb0484e9b818924feeb9add/CLOULD/386ba71cbf8c451288b899ec0d8f9fb1.html)

