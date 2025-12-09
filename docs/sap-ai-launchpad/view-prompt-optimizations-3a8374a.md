<!-- loio3a8374ae86f24783b6a0acc7ff3536fc -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# View Prompt Optimizations



<a name="loio3a8374ae86f24783b6a0acc7ff3536fc__section_vp3_r2g_s2c"/>

## Prerequisites

-   You have the `custom_evaluation`, `genai_manager` or `genai_experimenter` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

-   You have deployed a prompt optimization. For more information, see [Create a Prompt Optimization](create-a-prompt-optimization-0b920f6.md).

-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app and choose the resource group that was used for your generative AI hub deployment.

2.  In the side navigation, expand the *Generative AI Hub* and choose *Optimizations*.




<a name="loio3a8374ae86f24783b6a0acc7ff3536fc__section_pmz_fhp_hfc"/>

## Runs

You can filter by name or by using tags by using the <span class="SAP-icons-V5"></span> \(Filter\)icon. Your input must be an exact match.

Runs related to optimizations workflows are labelled with “optimization” in the *Task* column.

You can select a prompt optimization run to see its details containing baseline scores, optimization scores and tags. For more information, see [View Prompt Optimization Run Details](view-prompt-optimization-run-details-acfce87.md).



<a name="loio3a8374ae86f24783b6a0acc7ff3536fc__section_sfj_fjd_w2c"/>

## Artifacts

The *Artifacts* tab lists your optimization artifacts.

To see an unfiltered list, use the *Clear All Filters* button.

To see prompt optimization artifacts only, filter by using the `genai-optimizations` scenario

You can search for an artifact using the search bar.

You can filter the list of artifacts using the <span class="SAP-icons-V5"></span> \(Filter\) icon. Text input must be an exact match.

