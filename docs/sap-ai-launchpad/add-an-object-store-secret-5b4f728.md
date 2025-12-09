<!-- loio5b4f728c8f21403697728687f96e03c6 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add an Object Store Secret

As an administrator, you can add object store secrets for use within your AI processes.



<a name="loio5b4f728c8f21403697728687f96e03c6__prereq_t21_cgz_qxb"/>

## Prerequisites

-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.
-   You have the `aicore_admin_objectstoresecret_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations).




<a name="loio5b4f728c8f21403697728687f96e03c6__context_vls_chz_qxb"/>

## Context

You can use the *SAP AI Core Administration* app to add secrets for multiple object stores. The object stores must already exist with valid credentials.

Supported cloud object stores include Amazon S3 \(S3\), Alibaba Cloud Object Storage Service \(OSS\), Azure, and SAP HANA Cloud, data lake \(WebHDFS\).



<a name="loio5b4f728c8f21403697728687f96e03c6__steps_zj5_dhz_qxb"/>

## Procedure

1.  In the *Workspaces* app, choose the AI API connection and resource group.

2.  Open the *SAP AI Core Administration* app and choose *Object Store Secrets*.

    The *Object Store Secrets* screen appears with a tile for each existing secret.

3.  Choose *Add* to enter reference details for a new secret.

4.  Complete the fields in the *Add Object Store Secret* dialog box as follows:

    1.  Confirm the resource group. To change the resource group, choose <span class="SAP-icons-V5"></span> \(Change Value\).

    2.  Enter a name for the secret.

        Secret names must comply with the following criteria:

        -   Contain only lowercase alphanumeric characters, hyphens \(-\), or periods \(.\)

        -   Start with an alphanumeric character

        -   End with an alphanumeric character


    3.  Choose the type of object store.

    4.  Enter the path prefix. The path prefix is used to differentiate between different projects that are stored in the same location.

    5.  Complete the information requested in the dialog box.

        > ### Note:  
        > The type of object store determines what fields are required for the object store secret.

        For S3:

        -   Choose `Verify SSL` to apply the SSL security protocol to data transferred from the object store.
        -   Choose `Use HTTPS` to apply the HTTPS communication protocol to data transferred from the object store.

    6.  Enter the secret in `JSON` format. For more information, see [Register Your Object Store Secret](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/b083d73f672c428faac3048b74733546.html).


5.  Choose *Add* to save the secret details.




<a name="loio5b4f728c8f21403697728687f96e03c6__result_ibj_2hz_qxb"/>

## Results

The new secret appears on the *Object Store Secrets* screen.

The saved secret enables read access to the nominated hyperscaler object store, enabling stored files to be used in your launchpad processes.

