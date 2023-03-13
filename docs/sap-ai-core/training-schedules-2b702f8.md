<!-- loio2b702f8b3d0746f685ac4eea4eeb1755 -->

# Training Schedules

In order to run executions periodically, you can define an execution schedule that will start your exeuctions automatically. In order to schedule executions, you need to have prepared the configuration for the execution.

Training schedules have a start and end timestamp. The start timestamp defines when the schedule will first be run to generate executions. The end timestamp defines when the schedule will expire.

A schedule that has not yet expired has ACTIVE status. Upon expiry, the status will changed to INACTIVE, and no further executions will start.

The format for these timestamps is defined by RFC3339 section 5.6, without fractions of seconds, for example: `2023-02-09T12:53:47Z`. All timestamps are interpreted in UTC time. For more information, see [RFC3339 section 5.6](https://www.rfc-editor.org/rfc/rfc3339#section-5.6)and [About the AI API](about-the-ai-api-716d4c3.md).

-   **[Create a Training Schedule](create-a-training-schedule-bd409a9.md "")**  

-   **[List Executions Created by a Training Schedule](list-executions-created-by-a-training-schedule-2c1ecfb.md "")**  

-   **[Change an Exisitng Training Schedule](change-an-exisitng-training-schedule-18caf4b.md "")**  

-   **[Delete a Training Schedule](delete-a-training-schedule-9dc25e1.md "")**  


**Parent topic:** [Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Workflow Templates](workflow-templates-83523ab.md "Here, you can find a minimal workflow example template, that can be adapted to meet the requirements of your workflow.")

[List Scenarios](list-scenarios-deedde5.md "A scenario is a group of related executables for a use case within the user's tenant. A scenario can have multiple versions that further correspond to the different versions of executables.")

[List Executables](list-executables-80895a4.md "An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a scenario and get details of specific executables from a scenario. Workflow templates are mapped to training executables.")

[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references, and executables that are used to run an execution or deployment.")

[List Configurations](list-configurations-8074b2a.md "")

[Start Training](start-training-54b44e4.md "Start training and check the status of the execution.")

[Stop Training Instances](stop-training-instances-3d85344.md#loio3d853443027449d9a33723165b19b25a "")

[Delete Training Instances](delete-training-instances-612ce17.md#loio612ce172e609432a840a22eb211ecf7b "Deleting a training instance releases the SAP AI Core resources that it used.")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs.")

