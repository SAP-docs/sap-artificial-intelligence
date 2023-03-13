<!-- loioc02fca9f07f34511b86c2d4de0240bf1 -->

# Register an Other Artifact

Use the *ML Operations* app to manually register an other artifact that is stored in your object store.



<a name="loioc02fca9f07f34511b86c2d4de0240bf1__prereq_lmh_lrd_pea"/>

## Prerequisites

You have the `artifact.register` role, or you have been assigned a role collection that contains this role. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).

Details for the object store secret have been added using the *SAP AI Core Administration* app. See [Add an Object Store Secret](add-an-object-store-secret-5b4f728.md).



## Context

> ### Caution:  
> If the files for a registered artifact are deleted from your object store, if the datapath or object store secret changes, then the registered artifact can no longer be used.



<a name="loioc02fca9f07f34511b86c2d4de0240bf1__steps_qkj_n3p_pea"/>

## Procedure

1.  Choose the resource group. For more information, see [Set Resource Group](set-resource-group-0c07728.md#loio0c077289f29d4147921fb07ab0f68b7f).

2.  In the *ML Operations* app, choose *Other Artifacts*.

    The *Other Artifacts* screen appears listing all of the other typye artifacts for the selected resource group.

3.  Choose *Add* to manually register an artifact.

    The register artifact wizard appears. This wizard has five steps.

4.  Enter the details for the other artifact.

    1.  In the *Scenario* step, choose the scenario in which the artifact will be used.

    2.  In the *General Information* step, specify a name and description for the artifact.

    3.  In the *URL* step, enter the URL for the artifact in your object store.

        > ### Tip:  
        > URLs must adhere to the following convention `ai://<objectStore name>/<data path>`.

    4.  In the *Labels* \(Optional\) step, enter any labels and values that you would like to apply to the artifact.

    5.  In the *Review* step, confirm the details that you've provided for the artifact.


5.  Choose *Add* to complete artifact registration.




<a name="loioc02fca9f07f34511b86c2d4de0240bf1__result_twq_cvx_v5b"/>

## Results

The artifact that you have registered now appears in the list of other artifacts for the resource group.

**Related Information**  


[Create Artifacts](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/66413f1d9fbf4758a0d739eaf1c95dc7.html "Create an artifact to connect a dataset or model, to make it available for use in SAP AI Core.") :arrow_upper_right:

[Manage Object Store Secrets](manage-object-store-secrets-0377ede.md "You can connect your AI processes with a cloud object store, and manage access using an object store secret.")

