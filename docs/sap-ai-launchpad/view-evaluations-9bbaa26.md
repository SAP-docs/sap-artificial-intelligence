<!-- loio9bbaa26dbf9c4fb396f3aa9401e88947 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# View Evaluations



<a name="loio9bbaa26dbf9c4fb396f3aa9401e88947__section_vp3_r2g_s2c"/>

## Prerequisites

-   You have the `custom_evaluation`, `genai_manager` or `genai_experimenter` role, or you are assigned a role collection that contains one of these roles.

-   You have deployed an evaluation run. For more information, see [Create an Evaluation](create-an-evaluation-c15182a.md).

-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app and choose the resource group that was used for your generative AI hub deployment.

2.  In the side navigation, expand the *Generative AI Hub* and choose *Optimizations*.




<a name="loio9bbaa26dbf9c4fb396f3aa9401e88947__section_pmz_fhp_hfc"/>

## Runs

You can filter by name or by using tags by using the <span class="SAP-icons-V5"></span> \(Filter\)icon. Your input must be an exact match.

Runs related to evaluations workflows are labelled with “evaluation” in the *Task* column.

You can select an evaluation run to see its details containing meta data, metrics and tags for your evaluation.

You can view the result of your evaluation, For more information, see [View Evaluation Run Details](view-evaluation-run-details-fe6b3e9.md).

You can compare the metrics of multiple runs. For more information, see [Compare Runs](compare-runs-6dc7cb8.md).



<a name="loio9bbaa26dbf9c4fb396f3aa9401e88947__section_sfj_fjd_w2c"/>

## Artifacts

The *Artifacts* tab lists your optimization artifacts.

To see an unfiltered list, use the *Clear All Filters* button.

To see evaluation artifacts only, filter by using the `genai-evaluations` scenario

You can search for an artifact using the search bar.

You can filter the list of artifacts using the <span class="SAP-icons-V5"></span> \(Filter\) icon. Text input must be an exact match.



<a name="loio9bbaa26dbf9c4fb396f3aa9401e88947__section_sk1_hhp_hfc"/>

## Jobs

The*Jobs* tab lists your jobs and their details.

You can filter the list of jobs using the <span class="SAP-icons-V5"></span> \(Filter\) icon. Text input must be an exact match.

You can view the details of a job by selecting it from the list. For more information, see [View Evaluation Job Details](view-evaluation-job-details-200ccaf.md).

You can stop one or more job by using the checkboxes and choosing *Stop*.

You can delete one or more job by using the checkboxes and choosing *Delete*.

> ### Note:  
> Where jobs with a mixture of states that can be stopped **and** deleted are selected, only items eligible to the chosen request will be successfully processed.

