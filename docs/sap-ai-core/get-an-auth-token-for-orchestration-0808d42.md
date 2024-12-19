<!-- loio0808d423946141bca151356d995939f5 -->

# Get an Auth Token for Orchestration

<a name="task_dn3_jnn_fyb"/>

<!-- task\_dn3\_jnn\_fyb -->

## Using Postman



<a name="task_dn3_jnn_fyb__prereq_y3l_dz5_gpb"/>

## Prerequisites

-   You have downloaded and installed the Postman client from [https://www.postman.com/](https://www.postman.com/).
-   You have familiarized yourself with the Postman documentation and interface.



<a name="task_dn3_jnn_fyb__steps_zc4_cvn_fyb"/>

## Procedure

1.  Download the JSON collection from [Orchestration JSON](https://help.sap.com/doc/4207e502f8d641868dcc642a12635cfe/CLOUD/en-US).

2.  In Postman, click *Import*, select the JSON file, and choose *Import* to start the import.

3.  After the import is complete, expand the collection and navigate to *Get Auth Token*.

4.  Select the `LLM Orchestration` environment within Postman and configure it using the following values:

    -   The *LLM Orch Url* is the URL of your orchestration deployment. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).

    -   The *Client Id* is the XSUAA client id of your AI API connection.

    -   The *Client Secret* is the XSUAA client secret of your AI API connection.

    -   The *Grant Type* URL parameter should be set to `Client Credentials`.

    -   Leave the *Token* value empty.


5.  To retrieve an authentication token, send a GET request to `Auth Token`.

    The response includes an access token, which is saved as the *Token* variable in the Postman environment. Check that the access token has been added correctly to the variable and if not, copy and paste it from the response into the variable.




<a name="task_dn3_jnn_fyb__postreq_fjj_vmt_c1c"/>

## Next Steps

Send a POST request using the `Simple LLM Call` from the Postman collection to try out the templating mechanism of orchestration.

<a name="task_wqc_b4n_fyb"/>

<!-- task\_wqc\_b4n\_fyb -->

## Using Curl

Start by setting the required environment variables, which you can get from your SAP AI Core instance.



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
    AI_API_URL=<YOUR AI API URL>
    AUTH_URL=<YOUR AUTH URL>
    CLIENT_ID=<YOUR CLIENT ID>
    CLIENT_SECRET=<YOUR CLIENT SECRET>
    RESOURCE_GROUP=default
    ```

2.  Obtain the auth token by sending the following request:

    ```
    curl --request POST \
      --url "${AUTH_URL}/oauth/token" \
      --header 'content-type: application/x-www-form-urlencoded' \
      --data grant_type=client_credentials \
      --data client_id="$CLIENT_ID" \
      --data client_secret="$CLIENT_SECRET"
    ```

    The response includes an access token.

    ```
    {"access_token":"ey...", "expires_in":7199, "jti":"...", "token_type":"bearer"}
    ```

3.  Set the token to use it in the following steps:

    ```
    TOKEN=ey...
    
    ```


