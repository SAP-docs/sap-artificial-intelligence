<!-- loio6c07132751534c5288c29466b5d38f2c -->

# Delete a Deployment

You delete a deployment to remove it from your instance.



<a name="loio6c07132751534c5288c29466b5d38f2c__prereq_b54_nld_jpb"/>

## Prerequisites

You have either the `mloperations_editor` or `scenario_deployment_editor` role, or you are assigned to a role collection that contains one of these roles. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).



<a name="loio6c07132751534c5288c29466b5d38f2c__context_rxd_rnd_jpb"/>

## Context

Deployments are subject to quota limits. If you reach your quota limit, additional deployments can't be created and you'll be notified. You can free up your quota by deleting deployments that are no longer required.

You can delete a deployment if it has the status *Dead*, *Stopped*, or *Unknown*. For deployments in other statuses, the *Delete* button is not enabled.



<a name="loio6c07132751534c5288c29466b5d38f2c__steps_a1l_ynd_jpb"/>

## Procedure

1.  Navigate to the deployment's details. See [View a Deployment](view-a-deployment-d6f793e.md).

2.  Choose *Delete* in the header. A *Warning* dialog box appears.

3.  Choose *Delete* to confirm the deletion.




<a name="loio6c07132751534c5288c29466b5d38f2c__result_rr1_4nd_jpb"/>

## Results

The deployment is deleted, and its associated information is removed and cannot be retrieved.

> ### Note:  
> To create a deployment with the same settings \(model\) as the deleted deployment, you can use the same configuration to create a new deployment. The new deployment will have the same settings, however, it will generate a different endpoint \(URL\).

