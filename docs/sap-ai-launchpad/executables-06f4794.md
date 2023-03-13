<!-- loio06f4794caf9545bbb084611c1151ed8a -->

# Executables

An executable is used to define training or serving pipelines for an AI use case. Executables for the same AI use case are grouped by scenario.

> ### Example:  
> In SAP AI Core, an executable can be a template. For more information, see [Templates](https://help.sap.com/viewer/808d9d442fb0484e9b818924feeb9add/LATEST/en-US/8a1f91a18cf0473e8689789f1636675a.html).
> 
> In SAP AI Core, an executable can be a template. For more information, see [Templates](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/LATEST/en-US/8a1f91a18cf0473e8689789f1636675a.html).

-   An executable that is used to train an AI model is called a workflow executable.

-   An executable that is used to serve \(deploy\) an AI model is called a serving executable.


Executables contain any number of placeholders, such as parameters \(for hyperparameters of the AI model\), input artifacts \(for datasets, models\), and output artifacts \(for models\). Placeholders make it easy for resource groups to implement the executable with their own datasets or parameters.

-   To display an executable, navigate to the scenario details screen and click on the executable's name. For more information, see [View a Scenario](view-a-scenario-6ef1b9a.md).

-   To use an executable, you combine values to input artifacts using a configuration. In a configuration, you set values for these placeholders. You can then start the training or deploying process by creating a instance using that configuration.

    You can also define *Labels* that can be associated with an executable to provide annotations. These labels are listed on the executables details screen along with *Input Artifacts*, *Parameters*, and *Output Artifacts*.

-   To use executables, you have either the `mloperations_viewer` or `scenario_executable_viewer` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).


> ### Example:  
> Consider a scenario, such as a Product Review Classification, involving positive or negative reviews.
> 
> This scenario has a workflow executable named ***Product\_Review\_Train*** with the following placeholders:
> 
> -   Input parameters
> 
>     -   `Num_of_epochs`
> 
>     -   `Max_Depth_Decision_Tree`
> 
> 
> -   Input artifacts
> 
>     -   `Stopwords_Dataset`
> 
>     -   `Past_Reviews`

-   **[Workflow Executables](workflow-executables-799bb31.md "An executable that is used to train an AI model or perform batch inferencing is called a
		workflow executable.")**  
An executable that is used to train an AI model or perform batch inferencing is called a workflow executable.
-   **[Serving Executables](serving-executables-4a55fb3.md "An executable that is used to deploy (serve) an AI model is called a serving
		executable.")**  
An executable that is used to deploy \(serve\) an AI model is called a serving executable.

**Related Information**  


[Executables](executables-06f4794.md "An executable is used to define training or serving pipelines for an AI use case. Executables for the same AI use case are grouped by scenario.")

[Serving Executables](serving-executables-4a55fb3.md "An executable that is used to deploy (serve) an AI model is called a serving executable.")

