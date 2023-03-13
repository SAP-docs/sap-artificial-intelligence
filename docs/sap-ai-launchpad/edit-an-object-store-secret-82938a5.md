<!-- loio82938a5503f44d57ae6a7019d7785821 -->

# Edit an Object Store Secret

As an administrator, you can edit object store secrets used within your AI processes.



<a name="loio82938a5503f44d57ae6a7019d7785821__prereq_oop_cq2_rob"/>

## Prerequisites

You have the `aicore_admin_objectstoresecret_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).

You have access to the hyperscaler object store over the Internet.



<a name="loio82938a5503f44d57ae6a7019d7785821__context_oop_pxq_ysb"/>

## Context

You edit a secret when its credentials \(user name and access token\) change.

> ### Note:  
> You cannot change the name or the resource group for a secret. If the name or resource group is no longer valid or contains errors, you'll need to remove the secret and re-create it with the correct details. See [Remove an Object Store Secret](remove-an-object-store-secret-775b306.md).



<a name="loio82938a5503f44d57ae6a7019d7785821__steps_oop_kgy_ysb"/>

## Procedure

1.  In the *Workspaces* app, choose the AI API connection.

2.  Open the *SAP AI Core Administration* app and choose *Object Store Secrets*.

    The *Object Store Secrets* screen appears with a tile for each existing secret.

3.  Find the tile for the secret and choose *Edit*.

    The *Edit Object Store Secret* dialog box appears.

4.  Change the secret details.

    1.  Edit the path prefix, if required. The path prefix is used to differentiate between different projects which are stored in the same location.

    2.  For ***S3*** object stores:

        -   Edit the bucket, endpoint, and region. The region is determined by your global account and indicates where your AI data is held.

        -   Choose ***Verify SSL*** to apply the SSL security protocol to data transferred from the object store.
        -   Choose ***Use HTTPS*** to apply the HTTPS communication protocol to data transferred from the object store.

    3.  Enter the secret in `JSON` format.


5.  Choose *Edit* to save the changes to the secret.




<a name="loio82938a5503f44d57ae6a7019d7785821__result_oop_yr4_xsb"/>

## Results

The updated secret appears on the *Object Store Secrets* screen.

