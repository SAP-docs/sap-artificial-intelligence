<!-- loio0543c2c28e344919b6f2792925b1501f -->

# Deployments

A deployment runs a model for serving \(inferencing\) purposes. You use deployments to make online predictions.

A serving executable is an AI pipeline that serves or deploys a model for online predictions. You use a configuration to specify values for the serving executable, such as the model as an input artifact. The configuration is then used to create a deployment.

A *running* deployment can only reference one configuration. However, you can create multiple configurations for use with a deployment. You can update a deployment whilst it is running to change the referenced configuration.

A deployment is an instance of a serving executable \(referenced in a configuration\). For more information, see [Configurations](configurations-3c9d504.md). Multiple deployments can be created using the same configuration, resulting in separate endpoints for online predictions.

You use SAP AI Launchpad to create deployments for your runtime connection. Deployments that are implemented on an SAP AI Core runtime produce `HTTPS` endpoints.



<a name="loio0543c2c28e344919b6f2792925b1501f__section_ezk_y5q_qtb"/>

## Custom Features

> ### Remember:  
> The features that you see in the user interface depend on the capability settings in your underlying runtime. For more information, see [Custom Runtime Capabilities Using the Meta API](custom-runtime-capabilities-using-the-meta-api-ac3d92b.md).



<a name="loio0543c2c28e344919b6f2792925b1501f__section_cm5_syx_qvb"/>

## Deployment Duration

If your runtime supports deployment durations \(such as SAP AI Core\), you'll be able to define durations for your deployments. The duration you nominate \(for example, two days\) is added to the deployment's creation timestamp. The deployment runs until this time. Deployments which are not finished by the running until time are automatically stopped and deleted.



<a name="loio0543c2c28e344919b6f2792925b1501f__section_hhs_pyz_abc"/>

## Deployment Quotas

Each tenant is assigned a default quota that limits the number of deployments and replicas per deployment. If you reach this quota, additional deployments can't be created, and you'll be notified. You can free up your quota by deleting deployments that are no longer required.



<a name="loio0543c2c28e344919b6f2792925b1501f__section_e53_c1p_def"/>

## Deployment Statuses

Deployments can have any of the following statuses:

-   Pending
-   Running
-   Stopping
-   Stopped
-   Dead
-   Unknown

When a deployment has a *running* status, it can be used to make predictions.

> ### Note:  
> A deployment with a *stopped* status cannot be restarted. To run a deployment again, create another deployment using the same configuration, and retain the combination of values for serving executable and model.

The following figure shows how deployment statuses change following the initial status of *Pending*:

  
  
**Deployment Status Flow**

![Architecture diagram showing system components and workflow](images/Deployments_State_Flow_0a118b8.png)

When a deployment leaves *Running* status, the computing resources that were used by the AI runtime are released.

**Stop/ Delete Behavior by Deployment Status**


<table>
<tr>
<th valign="top">

Status

</th>
<th valign="top">

Stop Deployment

</th>
<th valign="top">

Delete Deployment

</th>
</tr>
<tr>
<td valign="top">

Unknown

</td>
<td valign="top">

Not enabled

</td>
<td valign="top">

Enabled

</td>
</tr>
<tr>
<td valign="top">

Pending

</td>
<td valign="top">

Enabled

</td>
<td valign="top">

Not enabled

</td>
</tr>
<tr>
<td valign="top">

Running

</td>
<td valign="top">

Enabled

</td>
<td valign="top">

Not enabled

</td>
</tr>
<tr>
<td valign="top">

Stopping

</td>
<td valign="top">

Not enabled

</td>
<td valign="top">

Not enabled

</td>
</tr>
<tr>
<td valign="top">

Stopped

</td>
<td valign="top">

Not enabled

</td>
<td valign="top">

Enabled

</td>
</tr>
<tr>
<td valign="top">

Dead

</td>
<td valign="top">

Not enabled

</td>
<td valign="top">

Enabled

</td>
</tr>
</table>

-   **[Create a Deployment](create-a-deployment-33b34e9.md "You create a deployment to run a model for serving purposes.")**  
You create a deployment to run a model for serving purposes.
-   **[View a Deployment](view-a-deployment-d6f793e.md " You can view the lifecycle details for a deployment, and explore details for each operation in the deployment.")**  
 You can view the lifecycle details for a deployment, and explore details for each operation in the deployment.
-   **[Update a Deployment](update-a-deployment-bce2b16.md "You can update a deployment with your choice of configuration. ")**  
You can update a deployment with your choice of configuration.
-   **[View Status Details](view-status-details-7bda8db.md "You check a deployment's status details for detailed message, status, and severity information for a running deployment.")**  
You check a deployment's status details for detailed message, status, and severity information for a running deployment.
-   **[Stop a Deployment](stop-a-deployment-aa127da.md "Stopping a deployment releases the computing resources acquired in the runtime in which the deployment is present (such as SAP AI Core).")**  
Stopping a deployment releases the computing resources acquired in the runtime in which the deployment is present \(such as SAP AI Core\).
-   **[Stop Multiple Deployments](stop-multiple-deployments-d25b6b4.md "")**  

-   **[Delete a Deployment](delete-a-deployment-6c07132.md "You delete a deployment to remove it from your instance.")**  
You delete a deployment to remove it from your instance.
-   **[Delete Multiple Deployments](delete-multiple-deployments-148dc64.md "")**  

-   **[View Deployment Logs](view-deployment-logs-4f9682e.md "Deployment logs are generated by the code (in the AI pipeline template) which is deploying the model.")**  
Deployment logs are generated by the code \(in the AI pipeline template\) which is deploying the model.

**Related Information**  


[Configurations](configurations-3c9d504.md "Configurations combine artifacts (such as datasets or models) with executables, so that training or deployment processes can be undertaken.")

