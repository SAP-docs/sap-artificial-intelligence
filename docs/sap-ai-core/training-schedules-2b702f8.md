<!-- loio2b702f8b3d0746f685ac4eea4eeb1755 -->

# Training Schedules

In order to run executions periodically, you can define a schedule to start your executions automatically. To do this, you must have prepared your configuration for the execution.

Training schedules have a start and end timestamp. The start timestamp defines when the schedule will first be run to generate executions. The end timestamp defines when the schedule will expire.

A schedule that has not yet expired has ACTIVE status. Upon expiry, the status will changed to INACTIVE, and no further executions will start.

The format for these timestamps is defined by RFC3339 section 5.6, without fractions of seconds, for example: `2023-02-09T12:53:47Z`. All timestamps are interpreted in UTC time. For more information, see [RFC3339 section 5.6](https://www.rfc-editor.org/rfc/rfc3339#section-5.6)and [About the AI API](about-the-ai-api-716d4c3.md).

-   **[Create a Training Schedule](create-a-training-schedule-bd409a9.md "")**  

-   **[List Executions Created by a Training Schedule](list-executions-created-by-a-training-schedule-2c1ecfb.md "")**  

-   **[Change an Existing Training Schedule](change-an-existing-training-schedule-18caf4b.md "")**  

-   **[Delete a Training Schedule](delete-a-training-schedule-9dc25e1.md "")**  


**Parent topic:**[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Workflow Templates](workflow-templates-83523ab.md "Here, you can find a minimal workflow example template, that can be adapted to meet the requirements of your workflow.")

[List Scenarios](list-scenarios-deedde5.md "")

[List Executables](list-executables-80895a4.md "")

[Create Configurations](create-configurations-884ae34.md "")

[List Configurations](list-configurations-8074b2a.md "")

[Using Artifact Signatures](using-artifact-signatures-2f02a1d.md "Artifact signatures in the form of a hash can be added to output artifacts from executions.")

[Start Training](start-training-54b44e4.md "")

[Stop Training Instances](stop-training-instances-3d85344.md "")

[Delete Training Instances](delete-training-instances-612ce17.md "")

[Efficiency Features](efficiency-features-4cb76f7.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "accessed in the deployment and execution logs.")

