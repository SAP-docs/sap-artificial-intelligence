<!-- loiod346abdf6dfd48239e7503464ad38c27 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add a Secret

As a system administrator, you can add Docker registry secrets for use within your AI processes.



<a name="loiod346abdf6dfd48239e7503464ad38c27__prereq_g1f_qgx_rxb"/>

## Prerequisites

You have the `aicore_admin_dockerregistrysecret_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations).

You have access to the Docker registry over the Internet.



<a name="loiod346abdf6dfd48239e7503464ad38c27__context_cjl_qgx_rxb"/>

## Context

You can use the *SAP AI Core Administration* app to add multiple secrets. The Docker registry must already exist with valid credentials.



<a name="loiod346abdf6dfd48239e7503464ad38c27__steps_nmq_qgx_rxb"/>

## Procedure

1.  In the *Workspaces* app, choose the AI API connection.

2.  Open the *SAP AI Core Administration* app and choose *Docker Registry Secrets*.

    The *Docker Registry Secrets* screen appears with a tile for each existing secret.

3.  Choose *Add* to enter reference details for a new secret.

4.  Complete the fields in the *Add a Docker Registry Secret* dialog box as follows:

    1.  Enter a name for the secret. This is your choice of identifier for your secret.

        Secret names must comply with the following criteria:

        -   Contain only lowercase alphanumeric characters, hyphens \(-\), or periods \(.\)

        -   Start with an alphanumeric character

        -   End with an alphanumeric character


    2.  Enter the Docker registry secret in `JSON` format.

        Use the secret that has been provided to you by your registry provider. You can copy and paste the secret data, or upload the secret from a file.

        -   To copy the secret, copy the contents of the `data` parameter, as provided to you. The secret is between the parentheses. Paste the data into the *Secret* field.

        -   To upload the secret as a `.TXT` or `JSON` file, choose <span class="SAP-icons-V5"></span> \(Upload\) . Search for and choose the secret from a local file. The file data then defaults to the *Secret* field.

            > ### Note:  
            > Files larger than 10 KB can't be uploaded.



5.  Choose *Add* to add the secret to your SAP AI Core instance.




<a name="loiod346abdf6dfd48239e7503464ad38c27__result_plw_qgx_rxb"/>

## Results

The new secret appears on the *Docker Registry Secrets* screen.

The saved credentials enable read-access to the Docker registry, thereby enabling the Docker image to be pulled when an execution or deployment is created.

**Related Information**  


[Create Your Docker Registry Secret](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/b29c7437a54f46f39c911052b05aabb1.html)

