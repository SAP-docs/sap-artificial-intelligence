<!-- loio8519d000994244cd869a642070e586d4 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Create a Custom Metric



<a name="loio8519d000994244cd869a642070e586d4__prereq_kzx_stb_kgc"/>

## Prerequisites

-   You have the `genai_manager` or `custom_evaluation` role, or you are assigned a role collection that contains one of these roles.

-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.



## Context

You can run evaluation jobs using system defined metrics. For more information, see [System Defined Metrics in SAP AI Core](https://help.sap.com/docs/AI_CORE/52b4adb30e6744709d6226d2b0659dea/2ac6a0896b474fe8b6ba614a7b724d58.html).

You only need to define a custom metric if you want to create a custom LLM-as-a-judge metric.



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app, and choose the resource group used for your generative AI hub deployment.

2.  In the side navigation, expand the *Generative AI Hub* and choose *Evaluations*.

3.  Choose the *Metric Evaluators* tab and choose *Create*.

    A wizard appears to guide you through the process of creating a custom metric.

4.  Complete the fields with information about your metric

    1.  Choose a scenario

    2.  Give your metric a name

    3.  **Optional:** Provide a description of your metric

    4.  Give your metric a type

    5.  Give your metric an evaluation method

    6.  Choose *Next*


5.  Complete the fields with your metric configuration

    1.  Choose at least one property

    2.  Choose a model to act as a judge and configure its parameters

    3.  Enter an evaluation task

    4.  Enter an evaluation definition

    5.  **Optional:** Enter your evaluation criteria

    6.  Enter at least one rating rubric

        You can add more rubrics using the :heavy_plus_sign: icon. You can delete rubrics using the :wastebasket: icon.

    7.  **Optional:** Describe any steps the judge model should follow

        You can add more steps using the :heavy_plus_sign: icon. You can delete steps using the :wastebasket: icon.

    8.  **Optional:** Set precedents by adding few shot examples

        You can add more examples using the :heavy_plus_sign: icon. You can delete examples using the :wastebasket: icon.

    9.  Choose *Review*


6.  To make changes, choose previous. To continue, choose *Create*.




## Next Steps

You can use your custom metric in an evaluation. For more information, see [Create an Evaluation](create-an-evaluation-c15182a.md).

