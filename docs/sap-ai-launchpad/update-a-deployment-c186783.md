<!-- loioc1867836472741c79f718409a46dfce1 -->

# Update a Deployment

You can update a deployment with your choice of configuration.



<a name="loioc1867836472741c79f718409a46dfce1__prereq_wmn_qhk_wqb"/>

## Prerequisites

You have the `scenario_deployment_viewer` or `scenario_deployment_editor` role, or you have been assigned a role collection that contains one of these roles.

For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).



<a name="loioc1867836472741c79f718409a46dfce1__context_a5b_b1q_vsb"/>

## Context

Multiple configurations can be associated with a deployment. However, a deployment can only use one configuration. When you update a deployment, you can choose to apply a new configuration, or re-use an older or previously used configuration. For example:

-   Your existing deployment serves models A and B, but now you'd like to replace model A with a new model C. You want to use the same deployment and perform inference using the existing deployment URL endpoint.

-   You want to update an existing deployment with new parameter bindings, such as number of replicas, autoscaling annotation, or ENV variables.


Deployments can only be updated if their status is *pending*, *running* or *dead*.

The updated deployment retains the inference URL. If you use a new deployment configuration, inference requests continue to work.



<a name="loioc1867836472741c79f718409a46dfce1__steps_h22_21q_vsb"/>

## Procedure

1.  Find the deployment and display its details. See [Investigate a Deployment](investigate-a-deployment-28463c4.md).

2.  Choose *Update* to display the *Update Deployment* dialog. All available configurations are listed. You can display summary details for each configuration, and use this information to compare details such as parameters and input artifacts.

    ![Screenshot with configurations to choose from in left panel and configuration details in the right panel](images/Image_AIL_FE_Deployments_Choose_Config_8f45a08.jpg)

3.  Select the required configuration from the list, and choose *Update* to update the deployment.

    > ### Tip:  
    > The system indicates the configuration which is already in use. You cannot update the deployment with this configuration.

4.  Check the *Deployment Details* screen, and confirm that the deployment is *running* with the selected configuration.

    > ### Note:  
    > If the update was not effective and the deployment status is *dead*, you'll receive an error message. The error message contains the configuration ID of the last configuration that resulted in a *running* deployment. You can update the deployment with this last configuration to effectively undo or rollback the error, and return the deployment to a *running* status.


