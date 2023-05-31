<!-- loioa63c2f56360d4174b2120383704ec15c -->

# Register a Dataset

Use the *ML Operations* app to manually register a dataset that is stored in your object store.



<a name="loioa63c2f56360d4174b2120383704ec15c__prereq_lmh_lrd_jab"/>

## Prerequisites

You have the `artifact.register` role, or you have been assigned a role collection that contains this role. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).

Details for the object store secret have been added using the *SAP AI Core Administration* app. See [Add an Object Store Secret](add-an-object-store-secret-5b4f728.md).



## Context

After you've registered a dataset, you can use it as input for configurations in the *ML Operations* app.

> ### Caution:  
> If the files for a registered dataset are deleted from your object store, or if the datapath or object store secret changes, then the registered dataset can no longer be used.



<a name="loioa63c2f56360d4174b2120383704ec15c__steps_qkj_n3p_noa"/>

## Procedure

1.  Choose the resource group. For more information, see [Set Resource Group](set-resource-group-0c07728.md#loio0c077289f29d4147921fb07ab0f68b7f).

2.  In the *ML Operations* app, choose *Datasets*.

    The *Datasets* screen appears listing all of the datasets for the selected resource group.

3.  Choose *Add* to manually register a dataset.

    The register dataset wizard appears. This wizard has five steps.

4.  Enter the details for the dataset.

    1.  In the *Scenario* step, choose the scenario in which the dataset will be used.

    2.  In the *General Information* step, specify a name and description for the dataset.

    3.  In the *URL* step, enter the URL for the dataset in your object store.

        > ### Tip:  
        > URLs must adhere to the following convention `ai://<objectStore name>/<data path>`.

    4.  In the *Labels* \(Optional\) step, enter any labels and values that you would like to apply to the dataset.

    5.  In the *Review* step, confirm the details that you've provided for the dataset.


5.  Choose *Add* to complete dataset registration.




<a name="loioa63c2f56360d4174b2120383704ec15c__result_twq_cvx_vpb"/>

## Results

The dataset that you have registered now appears in the list of datasets for the resource group.

**Related Information**  


[Create Files](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/66413f1d9fbf4758a0d739eaf1c95dc7.html "") :arrow_upper_right:

[Manage Object Store Secrets](manage-object-store-secrets-0377ede.md "You can connect your AI processes with a cloud object store, and manage access using an object store secret.")

