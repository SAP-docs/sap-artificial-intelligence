<!-- copy8deca749fae84b2fbeca1a11531f5a2d -->

# Choose a Resource Plan

You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.



<a name="copy8deca749fae84b2fbeca1a11531f5a2d__context_q1p_fpm_zqb"/>

## Context

Resource plans are used to select resources in workflow and serving templates. Different steps of a workflow can have different resource plans.

In general, if your workload needs GPU acceleration, you should use one of the GPU-enabled resource plans. Otherwise, choose a resource plan based on the anticipated CPU and memory need of your workloads.

Within SAP AI Core, the resource plan is selected via the `ai.sap.com/resourcePlan` label at pod level. It maps the selected resource plan and takes a string value, which can be any of the following resource plan IDs:

**Resource Plan Specifications for AWS**


<table>
<tr>
<th valign="top">

Resource Plan IDs



</th>
<th valign="top">

GPUs



</th>
<th valign="top">

CPU Cores



</th>
<th valign="top">

Memory GBs



</th>
<th valign="top">

Code to Allocate Resources

in Workflow Templates



</th>
</tr>
<tr>
<td valign="top">

Train-L



</td>
<td valign="top">

1 V100



</td>
<td valign="top">

7



</td>
<td valign="top">

55



</td>
<td valign="top">

`ai.sap.com/resourcePlan: train.l`



</td>
</tr>
<tr>
<td valign="top">

Infer-S



</td>
<td valign="top">

1 T4



</td>
<td valign="top">

3



</td>
<td valign="top">

10



</td>
<td valign="top">

`ai.sap.com/resourcePlan: infer.s`



</td>
</tr>
<tr>
<td valign="top">

Infer-M



</td>
<td valign="top">

1 T4



</td>
<td valign="top">

7



</td>
<td valign="top">

26



</td>
<td valign="top">

`ai.sap.com/resourcePlan: infer.m`



</td>
</tr>
<tr>
<td valign="top">

Infer-L



</td>
<td valign="top">

1 T4



</td>
<td valign="top">

15



</td>
<td valign="top">

58



</td>
<td valign="top">

`ai.sap.com/resourcePlan: infer.l`



</td>
</tr>
<tr>
<td valign="top">

Starter



</td>
<td valign="top">

–



</td>
<td valign="top">

1



</td>
<td valign="top">

3



</td>
<td valign="top">

`ai.sap.com/resourcePlan: starter`



</td>
</tr>
<tr>
<td valign="top">

Basic



</td>
<td valign="top">

–



</td>
<td valign="top">

3



</td>
<td valign="top">

11



</td>
<td valign="top">

`ai.sap.com/resourcePlan: basic`



</td>
</tr>
<tr>
<td valign="top">

Basic-8x



</td>
<td valign="top">

–



</td>
<td valign="top">

31



</td>
<td valign="top">

116



</td>
<td valign="top">

`ai.sap.com/resourcePlan: basic.8x`



</td>
</tr>
</table>

> ### Note:  
> There are limits to the default disk storage size for all of these nodes. Datasets that are loaded to the nodes will consume disk space. If you have large data sets \(larger than 30 GB\), or have large models, you may have to increase the disk size. To do so, use the persistent volume claim in Argo Workflows to specify the required disk size \(see [Volumes](https://argoproj.github.io/argo-workflows/walk-through/volumes/)\).

**Parent topic:** [Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

**Related Information**  


[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.")

[List Executables](list-executables-6af8e60.md "An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.")

[Deploy Models](deploy-models-dd16e8e.md "")

[Inferencing](inferencing-e348ecf.md "")

[Update a Deployment](update-a-deployment-9789ddd.md "")

[Stop Deployments](stop-deployments-b7d2577.md " ")

[Delete Deployments](delete-deployments-0193d17.md " ")

[Efficiency Features](efficiency-features-9fad26a.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs.")

 <a name="loiocf3a9a5bb3f1476caf3099281da96a67"/>

<!-- loiocf3a9a5bb3f1476caf3099281da96a67 -->

## Service Usage Reporting

Usage consumption of services is reported in the SAP BTP cockpit on the *Overview* page for your global account and on the *Overview* and *Usage Analytics* pages of your subaccount. The usage report lists usage in billable measures and nonbillable measures. Your final monthly bill is based on the billable measure only. Nonbillable measures sre displayed for reporting purposes only.

