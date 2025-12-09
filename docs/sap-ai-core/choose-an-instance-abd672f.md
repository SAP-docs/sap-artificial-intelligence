<!-- copyabd672fa709b430080ffe76a99f06cee -->

# Choose an Instance

You can configure SAP AI Core to use different infrastructure instances for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “instance types” and “resource plans” for this purpose.



## Context

You must choose at least one instance. If you select an instance type, a resource plan isn't required and vice versa.

> ### Tip:  
> `instanceType`s are recommended because they provide access to newer hardware and higher performance specifications compared to `resourcePlan`s.

Instance types amd resource plans and are used to select instances in workflow and serving templates. Different steps of a workflow can have different instances assigned.

In general, if your workload needs GPU acceleration, use one of the GPU-enabled instances. Otherwise, choose a plan based on the anticipated CPU and memory need of your workloads.

Within SAP AI Core, the instances are selected via the `ai.sap.com/instanceType` and `ai.sap.com/resourcePlan` labels at pod level. It maps the selected instance and takes a string value, which is the ID of the instance.

There are limits to the default disk storage size for all these nodes. Datasets that are loaded to the nodes consume disk space. If you have large data sets \(larger than 30 GB\), or have large models, you may have to increase the disk size. To do so, use the persistent volume claim in Argo Workflows to specify the required disk size \(see [Volumes](https://argoproj.github.io/argo-workflows/walk-through/volumes/)\).



## Instance Types



### Available Instance Types

For information about available instance types and their IDs, see SAP Note [3660109](https://me.sap.com/notes/3660109), or send a GET request to the following endpoint:

`$AI_API_URL/v2/admin/resources/instanceType`

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $AUTH\_TOKEN

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
</table>

For example:

> ### Sample Code:  
> ```
> curl GET "$AI_API_URL/v2/admin/resources/instanceType" \
> --header "Authorization: Bearer $TOKEN" \
> 
> ```



### Using an Instance Type

Within SAP AI Core, the instances are selected via the `ai.sap.com/instanceType` label in your workflow templates. It maps the selected resource and takes a string value, which is the ID of the instance.

> ### Restriction:  
> The `ai.sap.com/instanceType` label is only available as part of the “extended” service plan.
> 
> `ai.sap.com/resourcePlans` can be used with the “standard” service plan,
> 
> For more information, see [Resource Plans](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/choose-resource-plan-train?version=CLOUD&q=instance+types#resource-plans) and [Service Plans](service-plans-c7244c6.md).

The following snippet shows an example placement of the label in a workflow template:

```
kind: WorkflowTemplate
metadata: ...
spec:
   templates:
      - name: <template name>
        metadata:
           labels: |
               ai.sap.com/instanceType: <instanceType value>

               ...
```

The following snippet shows an example placement of the label in a serving template:

```
kind: ServingTemplate

metadata: ...
spec:
  inputs:
    parameters:
      ...
  template:
    ...
    metadata:
      ...
      labels: |
        ai.sap.com/instanceType: <yourChoiceOfInstanceType>
         ...
```

For more information about specifying an `ai.sap.com/instanceType` within a template, see [Workflow Templates](workflow-templates-83523ab.md) and [Serving Templates](serving-templates-20a8667.md).



## Resource Plans



### Available Resource Plans

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



### Using a Resource Plan

The following snippet shows an example placement of the label in a workflow template:

```
kind: WorkflowTemplate
metadata: ...
spec:
   templates:
      - name: <template name>
        metadata:
           labels: |
               ai.sap.com/resourcePlan: <resourcePlan value>
               ...
```

The following snippet shows an example placement of the label in a serving template:

```
kind: ServingTemplate
metadata: ...
spec:
  inputs:
    parameters:
      ...
  template:
    ...
    metadata:
      ...
      labels: |
        ai.sap.com/resourcePlan: <yourChoiceOfresourcePlan>
         ...
```

For more information about specifying a `ai.sap.com/resourcePlan` within a template, see [Workflow Templates](workflow-templates-83523ab.md) and [Serving Templates](serving-templates-20a8667.md).

<a name="loiocf3a9a5bb3f1476caf3099281da96a67"/>

<!-- loiocf3a9a5bb3f1476caf3099281da96a67 -->

## Service Usage Reporting

Usage consumption of services is reported in the SAP BTP cockpit on the *Overview* page for your global account and on the *Overview* and *Usage Analytics* pages of your subaccount. The usage report lists usage in billable measures and non-billable measures. Your final monthly bill is based on the billable measure only. Non-billable measures are displayed for reporting purposes only.

