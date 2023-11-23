<!-- loio82938a5503f44d57ae6a7019d7785821 -->

# Edit an Object Store Secret

As an administrator, you can edit object store secrets used within your AI processes.



<a name="loio82938a5503f44d57ae6a7019d7785821__prereq_v1z_23z_qxb"/>

## Prerequisites

You have the `aicore_admin_objectstoresecret_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations).

You have access to the hyperscaler object store over the Internet.



<a name="loio82938a5503f44d57ae6a7019d7785821__context_qsc_g3z_qxb"/>

## Context

You edit a secret when its credentials \(user name and access token\) change.

> ### Note:  
> You cannot change the name or the resource group for a secret. If the name or resource group is no longer valid or contains errors, you'll need to remove the secret and re-create it with the correct details. See [Remove an Object Store Secret](https://help.sap.com/docs/AI_LAUNCHPAD/92d77f26188e4582897b9106b9cb72e0/775b3068af37416caa3ac4122389ac66.html).



<a name="loio82938a5503f44d57ae6a7019d7785821__steps_zjs_g3z_qxb"/>

## Procedure

1.  In the *Workspaces* app, choose the AI API connection.

2.  Open the *SAP AI Core Administration* app and choose *Object Store Secrets*.

    The *Object Store Secrets* screen appears with a tile for each existing secret.

3.  Find the tile for the secret and choose *Edit*.

    The *Edit Object Store Secret* dialog box appears.

4.  Change the secret details.

    1.  Edit the path prefix, if required. The path prefix is used to differentiate between different projects which are stored in the same location.

    2.  Complete the information requested in the dialog box.

        For S3:

        -   Choose `Verify SSL` to apply the SSL security protocol to data transferred from the object store.
        -   Choose `Use HTTPS` to apply the HTTPS communication protocol to data transferred from the object store.

    3.  Enter the secret in `JSON` format. For more information, see [Register Your Object Store Secret](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/b083d73f672c428faac3048b74733546.html)


5.  Choose *Edit* to save the changes to the secret.




<a name="loio82938a5503f44d57ae6a7019d7785821__result_wtc_h3z_qxb"/>

## Results

The updated secret appears on the *Object Store Secrets* screen.

