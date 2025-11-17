<!-- loio8162c5df09e844688a72a74f53ea2972 -->

# Register a Model

Use the *ML Operations* app to manually register a model that is stored in your object store.



<a name="loio8162c5df09e844688a72a74f53ea2972__prereq_lmh_lrd_jpb"/>

## Prerequisites

You have the `artifact.register` role, or you have been assigned a role collection that contains this role. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

Details for the object store secret have been added using the *SAP AI Core Administration* app. See [Add an Object Store Secret](add-an-object-store-secret-5b4f728.md).



## Context

After you've registered a model, you can use it with deployments in the *ML Operations* app.

> ### Caution:  
> If the files for a registered model are deleted from your object store, or if the datapath or object store secret changes, then the registered model can no longer be used.



<a name="loio8162c5df09e844688a72a74f53ea2972__steps_qkj_n3p_noa"/>

## Procedure

1.  Choose the resource group. For more information, see [Set Resource Group](set-resource-group-0c07728.md#loio0c077289f29d4147921fb07ab0f68b7f).

2.  In the *ML Operations* app, choose *Models*.

    The *Models* screen appears listing all of the models for the selected resource group.

3.  Choose *Add* to manually register a model.

    The register model wizard appears. This wizard has five steps.

4.  Enter the details for the model.

    1.  In the *Scenario* step, choose the scenario in which the model will be used.

    2.  In the *General Information* step, specify a name and description for the model.

    3.  In the *URL* step, enter the URL for the model in your object store.

        > ### Tip:  
        > URLs must adhere to the following convention `ai://<objectStore name>/<data path>`.

    4.  In the *Labels* \(Optional\) step, enter any labels and values that you would like to apply to the model.

    5.  In the *Review* step, confirm the details that you've provided for the model.


5.  Choose *Add* to complete model registration.




<a name="loio8162c5df09e844688a72a74f53ea2972__result_twq_cvx_v5b"/>

## Results

The model's details screen appears. Unlike models that result from an execution, registered models don't contain source execution details. The model that you have registered is now available for use, and is listed with all the models for the resource group.

