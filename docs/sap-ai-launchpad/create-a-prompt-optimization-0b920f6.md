<!-- loio0b920f6222f443c5b13531f80e484910 -->

# Create a Prompt Optimization





<a name="loio0b920f6222f443c5b13531f80e484910__prereq_vp3_r2g_s2c"/>

## Prerequisites

-   You have the `genai_manager` or `custom_evaluation` role, or you are assigned a role collection that contains one of these roles.
-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.
-   You have an object store with the name `default`. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-9ee15fb.md).
-   You've prepared your prompt optimization dataset and registered it as an artifact. For more information, see [Register an Artifact for Optimizations](register-an-artifact-for-optimizations-06ec70c.md).
-   You've prepared a prompt template and your template is available in the prompt registry. For more information, see [Save a Template](save-a-template-49d4248.md).



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app, and choose the resource group used for your generative AI hub deployment.

2.  In the side navigation, expand the *Generative AI Hub* and choose *Optimization*.

3.  Choose *Create* and choose *Prompt Optimization* if prompted.

    A wizard appears to guide you through the process of creating a prompt optimization.

4.  Select your artifact by completing the input fields with details of your workflow and test data.

    1.  Choose a prompt template

    2.  **Optional:** Choose an origin model to establish a baseline.

    3.  Choose at least one target model.

    4.  Choose a dataset artifact

    5.  Provide the subpath to your test dataset, relative to your selected test dataset artifact URL

    6.  Choose *Next*


5.  Choose a metric from the available metrics:

    You can refine the selection by applying the filters.

6.  **Optional:** Add additional configuration such as prompt template name and version and configuration of advanced settings.

    You can auto generate the name and version by choosing *Auto Generate*.

7.  Review the details of your prompt optimization, and choose *Create*.

    Your prompt optimization job starts. It can take some time for your results to be calculated.




## Results

You can view your best optimized prompt candidate by viewing the run details It is stored as a child node of your prompt optimization job. For more information, see [View Prompt Optimizations](view-prompt-optimizations-3a8374a.md).

