<!-- loio2a858aed9c7b4d8598ecbc8f6982af31 -->

# Edit a Secret



<a name="loio2a858aed9c7b4d8598ecbc8f6982af31__prereq_iqk_3mx_rxb"/>

## Prerequisites

-   You have the role `aicore_admin_genericsecret_editor` or a role collection that contains it. For more information, see [Roles and Authorizations](https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations). You can change the secret credentials, but not the secret name or resource group. To change the secret name, delete the existing secret and create a new one.

-   You're using the SAP AI Core runtime.




<a name="loio2a858aed9c7b4d8598ecbc8f6982af31__steps_ztm_jmx_rxb"/>

## Procedure

1.  In the *Workspaces* app, choose the AI API connection.

2.  For secrets at the resource group level, choose your resource group. Alternatively, use the toggles in the header or dialog box, where the system prompts you to specify a resource group.

3.  Open the *SAP AI Core Administration* app and choose *Generic Secrets*.

4.  Find the tile for the secret and choose *Edit*.

    The *Edit Generic Secret* dialog box appears.

5.  Change the secret details. Enter the secret in `JSON` format. For example:

    ```
    {
    		"some-credential": "bXktc2VjcmV0LWNyZWRlbnRpYWw=",
    		"other-credentials": "bXktc2VjcmV0LW90aGVyLWNyZWRlbnRpYWw="
    		}
    ```

    > ### Note:  
    > The API expects sensitive data to be Base64-encoded. You can easily encode your data in Base64 format using the following command on Linux or MacOS: `echo -n 'my-sensitive-data' | base64`

    Add labels to your secrets. Labels are only required for specific services. They’re predefined and are outlined in the related documentation.




<a name="loio2a858aed9c7b4d8598ecbc8f6982af31__result_lfs_jmx_rxb"/>

## Results

The updated secret appears on the *Generic Secrets* screen.

