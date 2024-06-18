<!-- loio775b3068af37416caa3ac4122389ac66 -->

# Remove an Object Store Secret

As an administrator, you remove an object store secret when the name is no longer valid or contains errors, or if the secret is no longer required.



<a name="loio775b3068af37416caa3ac4122389ac66__prereq_fkm_s3z_qxb"/>

## Prerequisites

You have the `aicore_admin_objectstoresecret_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations).

You have access to the hyperscaler object store over the Internet.



<a name="loio775b3068af37416caa3ac4122389ac66__context_vkt_s3z_qxb"/>

## Context

You remove a secret if the name is no longer valid or contains errors, or if the secret is no longer required.



<a name="loio775b3068af37416caa3ac4122389ac66__steps_nxz_s3z_qxb"/>

## Procedure

1.  In the *Workspaces* app, choose the AI API connection.

2.  Open the *SAP AI Core Administration* app and choose *Object Store Secrets*.

    The *Object Store Secrets* screen appears with a tile for each existing secret.

3.  Find the tile for the secret and choose *Remove*.

    The *Remove Object Store Secret* dialog box appears.

4.  Choose *Remove* to confirm the removal, and remove the secret from your SAP AI Core instance.




<a name="loio775b3068af37416caa3ac4122389ac66__result_mgf_t3z_qxb"/>

## Results

The secret no longer appears on the *Object Store Secrets* screen. Any artifacts, such as models or datasets, which are stored in the hyperscaler object store are no longer available for use in your launchpad processes.

