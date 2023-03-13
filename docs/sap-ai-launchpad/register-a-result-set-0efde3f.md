<!-- loio0efde3f977b5459ebb1877e3f487fbeb -->

# Register a Result Set

Use the *ML Operations* app to manually register a result set that is stored in your object store.



<a name="loio0efde3f977b5459ebb1877e3f487fbeb__prereq_lmh_lrd_lab"/>

## Prerequisites

You have the `scenario_artifact_viewer` or `scenario_metric_viewer` role, or you have been assigned a role collection that contains one of these roles.

For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).

Details for the object store secret have been added using the *SAP AI Core Administration* app. See [Add an Object Store Secret](add-an-object-store-secret-5b4f728.md).



<a name="loio0efde3f977b5459ebb1877e3f487fbeb__context_uyk_cjy_v5b"/>

## Context

After you've registered a result set, you can use it in the *ML Operations* app.

> ### Caution:  
> If the files for a registered result set are deleted from your object store, or if the datapath or object store secret changes, then the registered result set can no longer be used.



<a name="loio0efde3f977b5459ebb1877e3f487fbeb__steps_qkj_n3p_noa"/>

## Procedure

1.  Choose the resource group. For more information, see [Set Resource Group](set-resource-group-0c07728.md#loio0c077289f29d4147921fb07ab0f68b7f).

2.  In the *ML Operations* app, choose *Result Sets*.

    The *Result Sets* screen appears listing all of the results sets for the selected resource group.

3.  Choose *Add* to manually register a result set.

    The register result set wizard appears. This wizard has five steps.

4.  Enter the details for the result set.

    1.  In the *Scenario* step, choose the scenario in which the result set will be used.

    2.  In the *General Information* step, specify a name and description for the result set.

    3.  In the *URL* step, enter the URL for the result set in your object store.

        > ### Tip:  
        > URLs must adhere to the following convention `ai://<objectStore name>/<data path>`.

    4.  In the *Labels* \(Optional\) step, enter any labels and values that you would like to apply to the result set.

    5.  In the *Review* step, confirm the details that you've provided for the result set.


5.  Choose *Add* to complete result set registration.




<a name="loio0efde3f977b5459ebb1877e3f487fbeb__result_twq_cvx_v5b"/>

## Results

The result set that you have registered now appears in the list of result sets for the resource group.

**Related Information**  


[Manage Object Store Secrets](manage-object-store-secrets-0377ede.md "You can connect your AI processes with a cloud object store, and manage access using an object store secret.")

