<!-- loio33b34e989bed46a9918479c428deb56d -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Create a Deployment

You create a deployment to run a model for serving purposes.



<a name="loio33b34e989bed46a9918479c428deb56d__prereq_gr4_zlb_wxb"/>

## Prerequisites

You have either the `mloperations_editor` or `scenario_deployment_editor` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).



<a name="loio33b34e989bed46a9918479c428deb56d__context_e1p_1mb_wxb"/>

## Context

If your runtime supports deployment durations, you'll be able to set a timeframe for your deployment to run. The duration is determined by adding the specified timeframe to the creation timestamp. Deployments run until this time and are then automatically stopped and deleted.



<a name="loio33b34e989bed46a9918479c428deb56d__steps_zgv_1mb_wxb"/>

## Procedure

1.  Select a resource group. For more information, see [Set Resource Group](set-resource-group-0c07728.md#loio0c077289f29d4147921fb07ab0f68b7f).

2.  In the *ML Operations* app, choose *Deployments*.

    The *All Deployments* screen appears listing all of the deployments for the selected resource group. Deployments are listed by ID, and with additional details such as configuration name and ID, current and target status, created on timestamp, and changed on timestamp.

3.  Choose *Create Deployment* to create a new deployment.

    The *Create Deployment* wizard appears. This wizard has five steps.

4.  Select the required data for the new deployment.

    1.  In the *Select Scenario* step, select the scenario from the list and choose *Next*.

    2.  In the *Select Executable* step, select the serving executable \(deployment template\) from the list and choose *Next*.
    3.  In the *Select Configuration* step, select the required configuration. The details for the selected configuration are displayed in the right pane. You can search the list by entering a configuration name or part of the name in the :mag: field.

        > ### Tip:  
        > When your runtime is SAP AI Core, this search is not case-sensitive. For other runtimes, search may be case-sensitive.

        > ### Tip:  
        > If there is no configuration which matches your data requirements, you can choose *create a configuration*. You'll be redirected to create a configuration, and the deployment you've started will be lost. When you have saved the new configuration, you can re-create the deployment using the new configuration. See [Create a Configuration](create-a-configuration-03bdcc7.md).

    4.  In the *Duration* step, select either the standard or custom duration.

        The standard duration defaults from your runtime. For example the standard duration in the SAP AI Core production environment is unlimited.

        If you choose a custom duration for the deployment, you can nominate a timeframe over minutes, hours, or days. When the running until time is reached, the deployment is stopped and deleted.

        > ### Tip:  
        > Your runtime can define minimum and maximum duration, which can be used to limit duration. For more information on the duration defined for the SAP AI Core runtime, see [AI API Runtime Capabilities Endpoint](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/716d4c38e3054c93a9d481b51cc66298.html#ai-api-runtime-capabilities-endpoint) and [Deploy Models](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/dd16e8ef75654dde831e7b812688e4fa.html?state=DRAFT&version=CLOUD).

        Choose *Review* to continue.

    5.  In the *Review* step, review the data that you've selected for the new deployment.

        > ### Remember:  
        > Once a deployment is created, its duration cannot be changed.

        Choose *Create* to create the deployment.





<a name="loio33b34e989bed46a9918479c428deb56d__result_pgb_bmb_wxb"/>

## Results

The new deployment is created and is now displayed in the *All Deployments* screen.

**Related Information**  


[View a Configuration](view-a-configuration-d3de4a4.md "A configuration consists of parameters and input artifact references for training or deployment processes.")

[Create a Configuration](create-a-configuration-03bdcc7.md "A configuration combines parameters, artifacts (for example, a dataset or model), and executables, that are used in training or deploying a model.")

