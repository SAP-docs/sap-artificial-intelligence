<!-- loiof91741ad784344aea092ffe0094276ec -->

# Delete Multiple Executions



<a name="loiof91741ad784344aea092ffe0094276ec__prereq_u4j_sld_nwb"/>

## Prerequisites

You have the `mloperations_editor` or `scenario_execution_editor` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).



<a name="loiof91741ad784344aea092ffe0094276ec__context_rpq_snd_nwb"/>

## Context

-   The maximum number of updates per request is 100.

-   Only *stopped*, *dead* or *unknown* executions or deployments can be deleted.

-   Only *running* or *pending* executions or deployments can be stopped.




## Procedure

1.  Choose a resource group. For more information, see [Set Resource Group](set-resource-group-0c07728.md#loio0c077289f29d4147921fb07ab0f68b7f).

2.  In the *ML Operations* app, choose *Executions*.

    The *Executions* screen appears listing all of the executions for the selected resource group. Executions are listed by ID, and with additional details such as Name,Current and Target Status, Created On timestamp, and Changed On timestamp.

3.  Choose the Executions you want to stop, using the checkboxes.

4.  Choose *Delete* in the header.




<a name="loiof91741ad784344aea092ffe0094276ec__result_rsd_sc4_4wb"/>

## Results

A dialog box appears, confirming how many of your selected executions will be deleted.

> ### Note:  
> Where executions or deployments with a mixture of states that can be stopped **and** deleted are selected, only items eligible to the chosen request will be successfully processed.

> ### Remember:  
> Deleting an execution doesn't delete the associated model or result sets.

