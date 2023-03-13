<!-- loioe60f102c5ca94f94b84e42b0a41f4117 -->

# Scenarios

A scenario in the *ML Operations* app is a collection of executables.

A scenario is a technical realization of a business AI use case \(for example, a recommendation system, a review classifier\).

An executable refers to a template for an AI pipeline, which means there are placeholders to set values in AI pipelines. An AI pipeline is a piece of code that trains AI models or deploy those models. A scenario is a group of executables \(AI pipelines\) to realize an AI use case.

A scenario is a collection of the following kinds of executables:

 Workflow executable
 :   An executable that trains an AI model. A file \(script\) to read datasets and generate a model after training. It can also be used for batch inferencing. For more information, see [Workflow Templates](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/83523ab8b49245bcbc9f1bf0969e32d8.html).

  Serving executable
 :   An executable that serves \(deploys\) an AI model. A file \(script\) to load an AI model and serve it for inferencing \(making predictions\). For more information, see [Serving Templates](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/20a8667ef19e4de59a4469cb542a7457.html).

 Scenario\(s\) and their contained executables are available across all resource groups. For more information about how to isolate datasets and models for the same scenario, see [Resource Groups](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/26c6c6b50e3f412f8bc0cd6a8ebdb850.html).

-   **[View a Scenario](view-a-scenario-6ef1b9a.md "You use the ML
                                    Operations app to
		list all scenarios for a selected connection.")**  
You use the *ML Operations* app to list all scenarios for a selected connection.
-   **[Executables](executables-06f4794.md "An executable is used to define training or serving pipelines for an AI use case.
		Executables for the same AI use case are grouped by scenario.")**  
An executable is used to define training or serving pipelines for an AI use case. Executables for the same AI use case are grouped by scenario.

