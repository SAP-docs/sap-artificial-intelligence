<!-- loio148dc64d7f4c405d863320cf5d5acf7d -->

# Delete Multiple Deployments



<a name="loio148dc64d7f4c405d863320cf5d5acf7d__prereq_u4j_sld_nwb"/>

## Prerequisites

You have the `mloperations_editor` or `scenario_deployment_editor` role, or you are assigned a role collection that contains this role. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).



<a name="loio148dc64d7f4c405d863320cf5d5acf7d__context_ds2_snd_nwb"/>

## Context

-   The maximum number of updates per request is 100.

-   Only *stopped*, *dead* or *unknown* executions or deployments can be deleted.

-   Only *running* or *pending* executions or deployments can be stopped.




<a name="loio148dc64d7f4c405d863320cf5d5acf7d__steps_adc_fsb_wxb"/>

## Procedure

1.  Choose a resource group. For more information, see [Set Resource Group](set-resource-group-0c07728.md#loio0c077289f29d4147921fb07ab0f68b7f).

2.  In the *ML Operations* app, choose *Deployments*.

    The *Deployments* screen appears listing all of the deployments for the selected resource group. Deployments are listed by ID, and with additional details such as Name,Current and Target Status, Created On timestamp, and Changed On timestamp.

3.  Choose the Deployments you want to stop, using the checkboxes.

4.  Choose *Delete* in the header.




<a name="loio148dc64d7f4c405d863320cf5d5acf7d__result_at3_fsb_wxb"/>

## Results

A dialog box appears, confirming how many of your selected deployments will be deleted.

> ### Note:  
> Where executions or deployments with a mixture of states that can be stopped **and** deleted are selected, only items eligible to the chosen request will be successfully processed.

