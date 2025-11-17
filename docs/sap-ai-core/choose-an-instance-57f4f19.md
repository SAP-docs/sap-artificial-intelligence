<!-- loio57f4f19d9b3b46208ee1d72017d0eab6 -->

# Choose an Instance

You can configure SAP AI Core to use different infrastructure instances for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” and “instance types” for this purpose.



## Context

You must choose at least one instance. If you select a resource plan, an instance type isn't required and vice versa.

Resource plans and instance types are used to select instances in workflow and serving templates. Different steps of a workflow can have different instances assigned.

In general, if your workload needs GPU acceleration, use one of the GPU-enabled instances. Otherwise, choose a plan based on the anticipated CPU and memory need of your workloads.

Within SAP AI Core, the instances are selected via the `ai.sap.com/resourcePlan` and `ai.sap.com/instanceType` labels at pod level. It maps the selected instance and takes a string value, which is the ID of the instance.

There are limits to the default disk storage size for all these nodes. Datasets that are loaded to the nodes consume disk space. If you have large data sets \(larger than 30 GB\), or have large models, you may have to increase the disk size. To do so, use the persistent volume claim in Argo Workflows to specify the required disk size \(see [Volumes](https://argoproj.github.io/argo-workflows/walk-through/volumes/)\).

Instance types are recommended because they provide access to newer hardware and higher performance specifications compared to resource plans.



## Instance Types

> ### Restriction:  
> Instance types are only available as part of the “extended” service plan. For more information on instances that can be used with the “standard” service plan, see [Resource Plans](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/choose-resource-plan-train?version=CLOUD&q=instance+types#resource-plans).

Within SAP AI Core, the instances are selected via the `ai.sap.com/instanceType` label in your workflow templates. It maps the selected resource and takes a string value, which is the ID of the instance

For information about available instance types and their IDs, see SAP Note [3660109](https://me.sap.com/notes/3660109), or send a GET request to the following endpoint:

`{{apiurl}}/v2/admin/resources/instanceType`

For example:

> ### Sample Code:  
> ```
> curl GET "$AI_API_URL/v2/admin/resources/instanceType" \
> --header "Authorization: Bearer $TOKEN" \
> 
> ```



## Resource Plans

Within SAP AI Core, the instances are selected via the `ai.sap.com/resourcePlan` label in your workflow templates. It maps the selected resource and takes a string value, which is the ID of the instance.

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

Code to Allocate instances

in Workflow Templates

</th>
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
</table>

> ### Note:  
> For the free service plan, only the Starter resource plan is available. Specifying other plans results in an error. For the standard service plan, all resource plans are available.

**Parent topic:**[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Workflow Templates](workflow-templates-83523ab.md "Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.")

[List Scenarios](list-scenarios-deedde5.md "A scenario is an implementation of a specific AI use case within a user's tenant. It consists of a pre-defined set of AI capabilities in the form of executables and templates.")

[List Executables](list-executables-80895a4.md "An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts (datasets or models) and parameters (custom key-pair values) that enable the template to be reused in different scenarios.")

[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references (such as datasets or models), and environment settings that are used to instantiate and run an execution or deployment of an executable or template.")

[List Configurations](list-configurations-8074b2a.md "")

[Using Artifact Signatures](using-artifact-signatures-2f02a1d.md "Artifact signatures in the form of a hash can be added to output artifacts from executions.")

[Start Training](start-training-54b44e4.md "")

[Stop Training Instances](stop-training-instances-3d85344.md "")

[Delete Training Instances](delete-training-instances-612ce17.md "")

[Efficiency Features](efficiency-features-4cb76f7.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "Deployment and execution logs contain information about API processing and metrics.")

[Training Schedules](training-schedules-2b702f8.md "")

<a name="loiocf3a9a5bb3f1476caf3099281da96a67"/>

<!-- loiocf3a9a5bb3f1476caf3099281da96a67 -->

## Service Usage Reporting

Usage consumption of services is reported in the SAP BTP cockpit on the *Overview* page for your global account and on the *Overview* and *Usage Analytics* pages of your subaccount. The usage report lists usage in billable measures and non-billable measures. Your final monthly bill is based on the billable measure only. Non-billable measures are displayed for reporting purposes only.

