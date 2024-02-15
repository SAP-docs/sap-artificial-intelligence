<!-- loio78d9a92e88154b4fa0a8c2a2fc06bb81 -->

# Stop Multiple Executions



<a name="loio78d9a92e88154b4fa0a8c2a2fc06bb81__prereq_u4j_sld_nwb"/>

## Prerequisites

You have the `mloperations_editor` or `scenario_execution_editor` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations).



<a name="loio78d9a92e88154b4fa0a8c2a2fc06bb81__context_mfl_snd_nwb"/>

## Context

-   The maximum number of updates per request is 100.

-   Only *stopped*, *dead* or *unknown* executions or deployments can be deleted.

-   Only *running* or *pending* executions or deployments can be stopped.




<a name="loio78d9a92e88154b4fa0a8c2a2fc06bb81__steps_nb4_lm3_wxb"/>

## Procedure

1.  Choose a resource group. For more information, see [Set Resource Group](https://help.sap.com/docs/AI_LAUNCHPAD/92d77f26188e4582897b9106b9cb72e0/0c077289f29d4147921fb07ab0f68b7f.html).

2.  In the *ML Operations* app, choose *Executions*.

    The *Executions* screen appears listing all of the executions for the selected resource group. Executions are listed by ID, and with additional details such as Name,Current and Target Status, Created On timestamp, and Changed On timestamp.

3.  Choose the Executions you want to stop using, the checkboxes.

4.  Choose *Stop* in the header.




<a name="loio78d9a92e88154b4fa0a8c2a2fc06bb81__result_qqs_mm3_wxb"/>

## Results

A dialog box appears, confirming how many of your selected executions will be stopped.

> ### Note:  
> Where executions or deployments with a mixture of states that can be stopped **and** deleted are selected, only items eligible to the chosen request will be successfully processed.

