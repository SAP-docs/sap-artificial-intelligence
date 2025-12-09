<!-- loioc15182a98b33428db562961cfe5bbc3a -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Create an Evaluation



<a name="loioc15182a98b33428db562961cfe5bbc3a__prereq_vp3_r2g_s2c"/>

## Prerequisites

-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.
-   You have the `genai_manager` or `custom_evaluation` role, or you are assigned a role collection that contains one of these roles.
-   You've prepared your evaluation files and registered them as an artifact. For more information, see [Register an Artifact for Optimizations](register-an-artifact-for-optimizations-06ec70c.md).
-   You've prepared your variable mapping. For more information, see [Variable Mappings in SAP AI Core](https://help.sap.com/docs/AI_CORE/52b4adb30e6744709d6226d2b0659dea/56727a392781470e926145571edcaf9f.html).
-   You have an object store with the name `default`. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-9ee15fb.md).
-   If you're creating an evaluation with a prompt template: you've prepared a prompt template. For more information, see [Prompt Experimentation](prompt-experimentation-384cc0c.md) and [Save a Template](save-a-template-49d4248.md).
-   If you're creating an evaluation with an orchestration configuration: you've prepared an orchestration configuration. For more information, see [Build Your Orchestration Workflow](build-your-orchestration-workflow-b7dc8b4.md) and [Save an Orchestration Config](save-an-orchestration-config-b687c7d.md).
-   If you want to use a custom LLM-as-a-judge metric: you've created a custom metric. For more information, see [Create a Custom Metric](create-a-custom-metric-8519d00.md).



<a name="loioc15182a98b33428db562961cfe5bbc3a__context_t1b_dzf_2fc"/>

## Context

> ### Tip:  
> Additional metrics are available for evaluation workflows that include an orchestration configuration.



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app, and choose the resource group used for your generative AI hub deployment.

2.  In the side navigation, expand the *Generative AI Hub* and choose *Optimization*.

3.  Choose *Create* and choose *Evaluation* if prompted.

    A wizard appears to guide you through the process of creating an evaluation job.

4.  Use the switch to choose an input type.

5.  Select your artifact by completing the input fields with details of your workflow and test data.

    1.  For *Prompt and Model* input type: Choose a prompt template and one or more models. Optionally, you can change the orchestration deployment from the selected default.

    2.  For *Orchestration Configuration* input type: Choose an orchestration configuration.

    3.  Choose your test dataset.

    4.  Use the switch to specify the file type

    5.  Provide the subpath to your test dataset, relative to your selected test dataset artifact URL

    6.  **Optional:** Specify the number of test samples.

        By doing so, you limit the number of rows from the test dataset that are included in the evaluation. If you don't restrict the number of test samples, all rows in the test dataset are used.

    7.  Choose *Next*


6.  Choose from the available metrics.

    You can refine the selection by applying the filters.

    To search for a metric by name, use the search bar.

    To view the details of a metric, see [View Metrics](view-metrics-98a63b9.md).



7.  **Optional:** Add additional configuration such as:

    1.  Adjust the number of repetitions

        Repetition count specifies the number of times the same input is submitted to the LLM to evaluate the consistency of LLM output. The minimum value is 1. The default is 1.

    2.  Add variable mappings.

        Variable mappings can be added in JSON format, or through the interface in list mode.

        By default, variable names in the prompt templates are matched against the field names in the test dataset. Where variable names and field names are mismatched, mapping is required.

        For more information, see [Variable Mappings in SAP AI Core](https://help.sap.com/docs/AI_CORE/52b4adb30e6744709d6226d2b0659dea/56727a392781470e926145571edcaf9f.html).

    3.  Add meaningful tags. You can add more tags using the :heavy_plus_sign: icon. You can delete tags using the :wastebasket: icon.

    4.  Choose *Review*


8.  Review the details of your evaluation job, and choose *Create* to create your job.

    Your evaluation job starts. It can take some time for your results to be calculated.




<a name="loioc15182a98b33428db562961cfe5bbc3a__postreq_xby_2bn_s2c"/>

## Next Steps

You can check the status of the evaluation job status for your evaluation in the *Jobs* tab of the *Optimizations* app. For more information, see [View Evaluations](view-evaluations-9bbaa26.md).

When your evaluation job status is complete, you can view your results. For more information, see [View Evaluation Run Details](view-evaluation-run-details-fe6b3e9.md).

You can reuse your configuration by navigating to it in the *Configurations* area of the *ML Ops* app and choosing *Create Execution*.

