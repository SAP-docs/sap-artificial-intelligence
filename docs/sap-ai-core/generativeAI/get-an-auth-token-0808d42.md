<!-- loio0808d423946141bca151356d995939f5 -->

# Get an Auth Token

Authentication token retrieval enables secure access to your SAP instance. Set environment variables and use curl commands to obtain and use an access token. Use this process to authenticate API requests in subsequent steps.



<a name="loio0808d423946141bca151356d995939f5__prereq_olk_3l5_fyb"/>

## Prerequisites

-   curl is installed on your operating system.
-   You have the following values from your service key:
    -   AI API URL
    -   Authentication URL
    -   Client ID
    -   Client secret


curl is installed on your operating system.



## Context

Start by setting the required environment variables, which you can get from your SAP AI Core instance.



<a name="loio0808d423946141bca151356d995939f5__steps_vfc_dnv_gpb"/>

## Procedure

1.  Set up your environment as follows:

    ```
    AI_API_URL=<YOUR AI API URL>
    AUTH_URL=<YOUR AUTH URL>
    CLIENT_ID=<YOUR CLIENT ID>
    CLIENT_SECRET=<YOUR CLIENT SECRET>
    RESOURCE_GROUP=default
    ```

2.  Obtain the authentication token by sending the following request:

    ```
    SECRET=`echo -n "$CLIENTID:$CLIENTSECRET" | base64 -i - ` 
    TOKEN=`curl --request POST \
      --url "$AUTH_URL/oauth/token" \
      --header "Content-Type: application/x-www-form-urlencoded" \
      --data "grant_type=client_credentials" \
      --data "client_id=$CLIENTID" \
      --data "client_secret=$CLIENTSECRET"'
    ```

    The response includes an access token.

    ```
    {"access_token":"ey...", "expires_in":7199, "jti":"...", "token_type":"bearer"}
    ```

3.  Set the token to use it in the following steps:

    ```
    TOKEN=ey...
    
    ```


