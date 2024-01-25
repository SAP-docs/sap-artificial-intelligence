<!-- loio3a97465bf6164400a4b5c1641007e3d6 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Use a Service Key

**Parent topic:**[Initial Setup](initial-setup-38c4599.md "You provision SAP AI Core from the SAP BTP cockpit in SAP Business Technology Platform. After provisioning, you will have your service key, which provides URLs and credentials for accessing the SAP AI Core instance")

**Next:**[Create a Service Key](create-a-service-key-7323ff4.md "")

**Previous:**[SAP AI Core Starter Tutorials](sap-ai-core-starter-tutorials-9795b63.md "")

<a name="task_cqr_b4n_fyb"/>

<!-- task\_cqr\_b4n\_fyb -->

## Using SAP AI Launchpad



<a name="task_cqr_b4n_fyb__prereq_knz_l1p_fyb"/>

## Prerequisites

You have the `connections_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations).



<a name="task_cqr_b4n_fyb__steps_jvk_q1p_fyb"/>

## Procedure

1.  Open the *Workspaces* app and choose *Add*. The *Create AI API Connection* dialog appears.

2.  Enter a name for your new connection.

    Connection names must comply with the following criteria:

    -   Contain only lowercase alphanumeric characters, hyphens \(-\), or periods \(.\)

    -   Start with an alphanumeric character

    -   End with an alphanumeric character


3.  Upload the service key file for your SAP AI Core instance, if available.

    To upload the service key as a `.TXT` or `JSON` file, choose <span class="SAP-icons"></span> \(Upload\) . Search for and choose the local service key file.

    Service key data then defaults to the remaining fields.

    ![Create AI API Connection dialog with upload highlighted.](images/Image_AIL_MLOps_Connection_Upload_61d94f3.png)

4.  If a service key file is not available, complete the following:

    1.  Enter the `AI_API_URL` from your service key for your SAP AI Core instance.

    2.  Enter the `url` from your service key for your SAP AI Core instance.

    3.  Enter the `clientid` from your service key for your SAP AI Core instance.

    4.  Enter the `clientsecret` from your service key for your SAP AI Core instance.


    Sensitive fields are masked. You can unmask to show your entry if needed.

5.  Choose *Create*.




<a name="task_cqr_b4n_fyb__result_aj3_s1p_fyb"/>

## Results

The new connection appears in the *Workspaces* app.

<a name="task_dn3_jnn_fyb"/>

<!-- task\_dn3\_jnn\_fyb -->

## Using Postman



<a name="task_dn3_jnn_fyb__prereq_y3l_dz5_gpb"/>

## Prerequisites

-   You have downloaded and installed the Postman client from [https://www.postman.com/](https://www.postman.com/).
-   You have familiarized yourself with the Postman documentation and interface.



<a name="task_dn3_jnn_fyb__steps_zc4_cvn_fyb"/>

## Procedure

1.  Download the JSON collection from the [https://api.sap.com/api/AI\_CORE\_API/overview](https://api.sap.com/api/AI_CORE_API/overview).

2.  In Postman, press *Import* and choose the JSON file download. Double-click, then choose *Import* to start the import.

3.  After the import is complete, highlight the collection, then select the *Authorization* tab.

4.  Navigate to *Configure New Token*, enter the credentials from your service key and choose save.

    > ### Note:  
    > -   The *Token Name* field is your choice of descriptive identifier.
    > 
    > -   The *Access Token URL* is labelled *url* in your service key. Add `/oauth/token` to the end of the url.
    > 
    > -   The *Grant Type* should be `Client Credentials`.
    > 
    > 
    > You might see an alert relating to the characters in your credentials, you can ignore this.

5.  Select the *Variables* tab, and set your `baseUrl` from your credentials.

    The `baseUrl` is labelled *AI\_API\_URL* in your service key.

6.  Choose *Save*.

7.  In the *Authorization* tab, choose *Get New Access Token*. and wait for the authentication process.

    When the authentication process is comeplete, select *Use Token* to finish. Check that the token is stored in your environment variables. If it is not stored automatically, you can copy and paste it to the *Token* field manually.


<a name="task_wqc_b4n_fyb"/>

<!-- task\_wqc\_b4n\_fyb -->

## Using Curl



<a name="task_wqc_b4n_fyb__prereq_olk_3l5_fyb"/>

## Prerequisites

curl is likely to be installed on your operating system by default. To check, open a command prompt and enter `curl -V`. If curl isn't installed, download and install it from [https://curl.se/](https://curl.se/).

> ### Note:  
> On macOS, you may need to install `jq` so that you can follow the curl commands.
> 
> 1.  Install brew from [https://brew.sh/](https://brew.sh/).
> 
> 2.  In a Terminal session, run `brew install jq` to install `jq` in your shell environment.



<a name="task_wqc_b4n_fyb__steps_vfc_dnv_gpb"/>

## Procedure

1.  Set up your environment as follows:

    ```
    # XSUAA details 
    # URLs should be without trailing slash '/'
    export CLIENTID=<clientid> from service key
    export CLIENTSECRET=<clientsecret> from service key
    export XSUAA_URL=<url> from service key
    export AI_API_URL=<AI_API_URL> from service key
    
    ```

    > ### Note:  
    > The `export` command sets the values of your keys to your environment variable, meaning that they will be retained after you close your terminal session. It is possible to set the environment variables without the `export`, for the current session only.

2.  Get the XSUAA OAuth Token using `clientid` and `clientsecret` from the service key to call the APIs.

    The XSUAA OAuth token is required for authentication when making AI API calls.

    ```
    SECRET=`echo -n ‘$CLIENTID:$CLIENTSECRET’ | base64 -i - ` 
    TOKEN=`curl --location --request POST "$XSUAA_URL/oauth/token?grant_type=client_credentials" \ 
     --header "Authorization: Basic $SECRET" | jq -r '.access_token'` 
    
    ```

    > ### Note:  
    > The token is valid for a limited time. Once it has expired, create a new token, using the same code snippet.

3.  Verify that the token has been fetched properly:

    ```
    echo $TOKEN
    
    ```

    You should see a long string of alphnumeric characters:

    ```
    eyJhbGciOiJSUzI1NiIsImprdSI6Imh0dHBzOi8vYWktYWxwaGEtdmFsaWRhdGlvbi0yLmF1dGhlbnRpY2F0aW9uLnNhcC5oYW5hLm9uZGVtYW5kLmNvbS90b2tlbl9rZXlzIiwia2lkIjoiZGVmYXVsdC1qd3Qta2V5LTMyODMxMjg2NCIsInR5cCI6IkpXVCJ94ZGU5YjAxNmQ0MDk5YjlmM... 
    ............................................. 
    ...ALdfbMsHoYTtF6fNFbf3ZQ
    
    ```

