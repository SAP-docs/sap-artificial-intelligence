<!-- loio3a97465bf6164400a4b5c1641007e3d6 -->

# Use a Service Key

After you have created your service key, it can be used by local clients, apps in other spaces, or entities outside your deployment to access SAP AI Core through one of the available interfaces.

<a name="task_dn3_jnn_fyb"/>

<!-- task\_dn3\_jnn\_fyb -->

## Using a Third-Party API Platform



<a name="task_dn3_jnn_fyb__prereq_y3l_dz5_gpb"/>

## Prerequisites

-   You have downloaded and installed the API platform of your choice.
-   You have familiarized yourself with the documentation and interface of the platform.



<a name="task_dn3_jnn_fyb__steps_zc4_cvn_fyb"/>

## Procedure

1.  Download the JSON collection from [https://api.sap.com/api/AI\_CORE\_API/overview](https://api.sap.com/api/AI_CORE_API/overview).

2.  Import the JSON file to the API platform.

3.  After the import is complete, highlight the collection and select the *Authorization* tab.

4.  Navigate to *Configure New Token*, enter the credentials from your service key, and save your changes.

    > ### Note:  
    > -   The *Token Name* field is your choice of descriptive identifier.
    > 
    > -   The *Access Token URL* is labeled *url* in your service key. Add `/oauth/token` to the end of the URL.
    > 
    > -   The *Grant Type* should be `Client Credentials`.
    > 
    > 
    > If you see an alert relating to the characters in your credentials, ignore it.

    > ### Note:  
    > If you have generated a x.509 certificate instead of client secret credentials, you'll need to use your `certificate`, `key` and `certUrl` to create your token.
    > 
    > For example: `curl --cert <cert.pem> --key <key.pem> -XPOST <certUrl>/oauth/token -d 'grant_type=client_credentials&client_id=<client id>'`

5.  Select the *Variables* tab, and set your `baseUrl` from your credentials.

    The `baseUrl` is labeled *AI\_API\_URL* in your service key.

6.  Choose *Save*.

7.  In the *Authorization* tab, choose *Get New Access Token*. and wait for the authentication process.

    When the authentication process is complete, select *Use Token* to finish. Check that the token is stored in your environment variables. If it is not stored automatically, you can copy and paste it to the *Token* field manually.




<a name="task_dn3_jnn_fyb__postreq_fjj_vmt_c1c"/>

## Next Steps

To train and deploy your own AI models, follow the procedure in [Administration](administration-7937fc1.md).

To use generative AI models provided in the generative AI hub, see [Generative AI Hub](generative-ai-hub-7db524e.md).

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

    **For Linux:**

    ```
    # XSUAA details 
    # URLs should be without trailing slash '/'
    export CLIENTID=<clientid> from service key
    export CLIENTSECRET=<clientsecret> from service key
    export XSUAA_URL=<url> from service key
    export AI_API_URL=<AI_API_URL> from service key
    
    ```

    **For Windows PowerShell:**

    ```
    $env:CLIENTID = <clientid> from service key
    $env:CLIENTSECRET = <clientsecret> from service key
    $env:XSUAA_URL = <url> from service key
    $env:AI_API_URL = <AI_API_URL> from service key
    ```

    > ### Note:  
    > The `export` command sets the values of your keys to your environment variable, meaning that they will be retained after you close your terminal session. It is possible to set the environment variables without the `export`, for the current session only.

2.  Get the XSUAA OAuth Token using `clientid` and `clientsecret` from the service key to call the APIs.

    The XSUAA OAuth token is required for authentication when making AI API calls.

    **For Linux:**

    ```
    SECRET=`echo -n "$CLIENTID:$CLIENTSECRET" | base64 -i - ` 
    TOKEN=`curl --request POST \
      --url "$XSUAA_URL/oauth/token" \
      --header "Content-Type: application/x-www-form-urlencoded" \
      --data "grant_type=client_credentials" \
      --data "client_id=$CLIENTID" \
      --data "client_secret=$CLIENTSECRET"`
    ```

    **For Windows PowerShell:**

    ```
    $SECRET = $env:CLIENTID + ":" + $env:CLIENTSECRET
    $base64SECRET = [Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes($SECRET))
    $TOKENRESPONSE = Invoke-WebRequest -Method Post "$env:XSUAA_URL/oauth/token" -Headers @{ "Authorization" = "Basic $base64SECRET"; "Content-Type" = "application/x-www-form-urlencoded" } -Body "grant_type=client_credentials"
    $TOKENJSON = $TOKENRESPONSE.Content | ConvertFrom-Json
    $TOKEN = $TOKENJSON.access_token
    ```

    > ### Note:  
    > The token is valid for a limited time. Once it has expired, create a new token, using the same code snippet.

    > ### Note:  
    > If you have generated a x.509 certificate instead of client secret credentials, you'll need to use your `certificate`, `key` and `certUrl` to create your token.
    > 
    > For example: `curl --cert <cert.pem> --key <key.pem> -XPOST <certUrl>/oauth/token -d 'grant_type=client_credentials&client_id=<client id>'`

3.  Verify that the token has been fetched properly:

    ```
    echo $TOKEN
    
    ```

    You should see a long string of alphanumeric characters:

    ```
    eyJhbGciOiJSUzI1NiIsImprdSI6Imh0dHBzOi8vYWktYWxwaGEtdmFsaWRhdGlvbi0yLmF1dGhlbnRpY2F0aW9uLnNhcC5oYW5hLm9uZGVtYW5kLmNvbS90b2tlbl9rZXlzIiwia2lkIjoiZGVmYXVsdC1qd3Qta2V5LTMyODMxMjg2NCIsInR5cCI6IkpXVCJ94ZGU5YjAxNmQ0MDk5YjlmM... 
    ............................................. 
    ...ALdfbMsHoYTtF6fNFbf3ZQ
    
    ```




<a name="task_wqc_b4n_fyb__postreq_h25_3nt_c1c"/>

## Next Steps

To train and deploy your own AI models, follow the procedure in [Administration](administration-7937fc1.md).

To use generative AI models provided in the generative AI hub, see [Generative AI Hub](generative-ai-hub-7db524e.md).

