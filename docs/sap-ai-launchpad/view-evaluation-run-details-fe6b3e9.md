<!-- loiofe6b3e9621a041239c272cb1763d5802 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# View Evaluation Run Details



<a name="loiofe6b3e9621a041239c272cb1763d5802__prereq_vp3_r2g_s2c"/>

## Prerequisites

-   You have the `custom_evaluation`, `genai_manager` or `genai_experimenter` role, or you are assigned a role collection that contains one of these roles.

-   You have deployed an evaluation run. For more information, see [Create an Evaluation](create-an-evaluation-c15182a.md).

-   You're using the `extended` service plan. For more information, see [Service Plans](service-plans-ec1717d.md).



<a name="loiofe6b3e9621a041239c272cb1763d5802__context_cz1_51m_52c"/>

## Context

The evaluation job will calculate and report the aggregate job statistics for each completion.

Aggregate job statistics include the following:


<table>
<tr>
<th valign="top">

Statistic

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

average\_latency

</td>
<td valign="top">

The average time taken in seconds to get a completion from the orchestration service

</td>
</tr>
<tr>
<td valign="top">

completion\_count

</td>
<td valign="top">

Number of completions evaluated

</td>
</tr>
<tr>
<td valign="top">

total\_prompt\_tokens

</td>
<td valign="top">

Sum of prompt\_tokens of completions

</td>
</tr>
<tr>
<td valign="top">

total\_completion\_tokens

</td>
<td valign="top">

Sum of completion\_tokens of completions

</td>
</tr>
</table>



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app and choose the resource group that was used for your generative AI hub deployment.

2.  In the side navigation, expand the *Generative AI Hub* and choose *Optimizations*.

3.  Choose the *Runs* tab and select name of the evaluation that you want to view.

    Runs related to evaluations workflows are labelled with “evaluation” in the *Task* column.

    You can filter by name or by using tags by using the <span class="SAP-icons-V5"></span> \(Filter\)icon. Your input must be an exact match.

    The *Run Details* will open, containing meta data, metrics and tags for your evaluation.




<a name="loiofe6b3e9621a041239c272cb1763d5802__postreq_nnz_tjg_s2c"/>

## Next Steps

You can refresh the view using the <span class="SAP-icons-V5"></span> \(Refresh\) icon.

You can add more categorical metrics to your view using the :heavy_plus_sign: icon.

You can edit the values of existing tags using the :pencil2: icon, and delete existing tags using the :wastebasket: icon.

You can delete an evaluation using the *Delete* button.

You can create a duplicate evaluation job by choosing the *Duplicate* button.

**Related Information**  


[Compare Runs](compare-runs-6dc7cb8.md "")

