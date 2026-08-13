<!-- loio0b920f6222f443c5b13531f80e484910 -->

# Create a Prompt Optimization





<a name="loio0b920f6222f443c5b13531f80e484910__prereq_vp3_r2g_s2c"/>

## Prerequisites

-   You have the `genai_manager` or `custom_evaluation` role, or you are assigned a role collection that contains one of these roles.
-   You're using the `extended` service plan. For more information, see [Service Plans](service-plans-ec1717d.md).
-   You have an object store with the name `default`. For more information, see [Add an Object Store for Optimizations](add-an-object-store-for-optimizations-9ee15fb.md).
-   You've prepared your prompt optimization dataset and registered it as an artifact. For more information, see [Add an Artifact for Optimizations](add-an-artifact-for-optimizations-06ec70c.md).
-   You've prepared a prompt template and your template is available in the prompt registry. For more information, see [Save a Template](save-a-template-49d4248.md).



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app, and choose the resource group used for your generative AI hub deployment.

2.  In the side navigation, expand the *Generative AI Hub* and choose *Optimizations*.

3.  Choose *Create* and choose *Prompt Optimization* if prompted.

    A wizard appears to guide you through the process of creating a prompt optimization.

4.  Select your artifact by completing the input fields with details of your workflow and test data.

    1.  Choose a prompt template

    2.  **Optional:** Choose an origin model to establish a baseline

    3.  Choose at least one target model

    4.  Use the switch to specify the dataset split type

    5.  Choose a dataset artifact

    6.  Use the switch to specify the file type

    7.  Provide the subpath to your test dataset, relative to your selected test dataset artifact URL

    8.  Choose *Next*


5.  Choose a metric from the available metrics:

    You can refine the selection by applying the filters

    To search for a metric by name, use the search bar

    To view the details of a metric, see [View Metric Details](view-metric-details-db90bc4.md).

6.  **Optional:** Add additional configurations such as prompt template name and version, variable mapping and configuration of advanced settings.

    Variable mapping enables you to align variable names between prompts and test datasets, ensuring correct data flow even when attribute names differ. Use this feature to resolve naming mismatches and maintain consistency in automated prompt optimization workflows.

    Variable mappings can be added in JSON format by using *JSON* switch, or through form filling, by using the *List* switch.

    For more information, see [Variable Mapping in SAP AI Core](https://help.sap.com/docs/AI_CORE/b9f48eb4a993445b863a55dd4d38f64d/bb3d4f87034e4995b5f17d3f2acc090e.html).

7.  Review the details of your prompt optimization, and choose *Create*.

    Your prompt optimization job starts. It can take some time for your results to be calculated.




## Results

You can view your best optimized prompt candidate by viewing the run details It is stored as a child node of your prompt optimization job. For more information, see [View Prompt Optimizations](view-prompt-optimizations-3a8374a.md).

