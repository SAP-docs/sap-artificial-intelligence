<!-- loioe5cce06c8662434abaee27e77b748259 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add a Secret



<a name="loioe5cce06c8662434abaee27e77b748259__prereq_bsm_2mx_rxb"/>

## Prerequisites

-   You have the `aicore_admin_genericsecret_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations).
-   You are using the SAP AI Core runtime.



<a name="loioe5cce06c8662434abaee27e77b748259__context_k5q_fmx_rxb"/>

## Context

You can use the *SAP AI Core Administration* app to add generic secrets.



<a name="loioe5cce06c8662434abaee27e77b748259__steps_qcc_gmx_rxb"/>

## Procedure

1.  In the *Workspaces* app, choose the AI API connection.

2.  If you want to add your secret at the resource group level, choose the resource group. Alternatively you can use the toggles in the header or dialog box, where you will be prompted to specify a resource group.

3.  Open the *SAP AI Core Administration* app and choose *Generic Secrets*.

    The *Generic Secrets* screen appears with a tile for each existing secret.

4.  Choose *Add* to enter reference details for a new secret.

5.  Complete the fields in the *Add Generic Secret* dialog box as follows:

    1.  Switch between tenant level and resource group level secrets

    2.  If your secret is at the resource group level: confirm the resource group. To change the resource group, choose <span class="SAP-icons-V5"></span> \(Change Value\).

    3.  Enter a name for the secret.

        Secret names must comply with the following criteria:

        -   Contain only lowercase alphanumeric characters, hyphens \(-\), or numbers

        -   Do not start or end with a hyphen \(-\)


    4.  Enter the secret in `JSON` format. For example:


    ```
    {
    		"some-credential": "bXktc2VjcmV0LWNyZWRlbnRpYWw=",
    		"other-credentials": "bXktc2VjcmV0LW90aGVyLWNyZWRlbnRpYWw="
    		}
    ```

    > ### Note:  
    > The API expects sensitive data to be Base64-encoded. You can easily encode your data in Base64 format using the following command on Linux or MacOS: `echo -n 'my-sensitive-data' | base64`

6.  Choose *Add* to save the secret details.




<a name="loioe5cce06c8662434abaee27e77b748259__result_s1w_gmx_rxb"/>

## Results

The new secret appears on the *Generic Secrets* screen.

