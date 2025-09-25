<!-- copy5ec7ec0626ed4b55a496a48feab2b56b -->

# Get an Auth Token

Start by setting the required environment variables, which you can get from your SAP AI Core instance.



<a name="copy5ec7ec0626ed4b55a496a48feab2b56b__prereq_olk_3l5_fyb"/>

## Prerequisites

curl is likely to be installed on your operating system by default. To check, open a command prompt and enter `curl -V`. If curl isn't installed, download and install it from [https://curl.se/](https://curl.se/).

> ### Note:  
> On macOS, you may need to install `jq` so that you can follow the curl commands.
> 
> 1.  Install brew from [https://brew.sh/](https://brew.sh/).
> 
> 2.  In a Terminal session, run `brew install jq` to install `jq` in your shell environment.



<a name="copy5ec7ec0626ed4b55a496a48feab2b56b__steps_vfc_dnv_gpb"/>

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
      --data 'grant_type=client_credentials' \
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


