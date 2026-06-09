<!-- copybc35bc7f090e48b79b253865050a5fdd -->

# Create a Generic Secret for Google Drive

Creates a generic secret with base64‑encoded credentials required to connect Google Drive to Document Grounding in SAP AI Core.



## Overview

Your cloud storage credentials are managed using secrets. Secrets enable secure connections across directories and tools without exposing credentials.



## Prerequisites

-   A resource group is created for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).



## Procedure

1.  Send a POST request to the endpoint `$AI_API_URL/v2/admin/secrets`.

    Include the following headers in your request:

    -   `AI_API_URL`: The base URL of your SAP AI Core environment.
    -   `{{access_token}}`: Your access token for SAP AI Core.

    Set the following header:

    -   `AI-Resource-Group`: <code><i class="varname">&lt;resource-group-for-grounding&gt;</i></code>. The operation is performed at the resource-group level.

    The following API request creates a generic secret with base64-encoded values, including client credentials and other required fields, to integrate grounding in the generative AI hub.




**Request Fields**

The following API request creates a generic secret with base64-encoded values required for integrating Google Drive with Document Grounding.


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`name`

</td>
<td valign="top">

Name of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

`authentication`

</td>
<td valign="top">

Base64-encoded value for `OAuth2ClientCredentials`

</td>
</tr>
<tr>
<td valign="top">

`description`

</td>
<td valign="top">

Base64-encoded description of the generic secret \(optional\)

</td>
</tr>
<tr>
<td valign="top">

`url`

</td>
<td valign="top">

Base64-encoded value of [https://googleapis.com/drive/v3](https://googleapis.com/drive/v3) 

</td>
</tr>
<tr>
<td valign="top">

`clientId`

</td>
<td valign="top">

Base64-encoded Client ID from the service account key JSON

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL`

</td>
<td valign="top">

Base64-encoded value of [https://oauth2.googleapis.com/token](https://oauth2.googleapis.com/token)

</td>
</tr>
<tr>
<td valign="top">

`private_key`

</td>
<td valign="top">

Base64-encoded Private Key from the service account key JSON

</td>
</tr>
<tr>
<td valign="top">

`client_email`

</td>
<td valign="top">

Base64-encoded Client Email from the service account key JSON

</td>
</tr>
<tr>
<td valign="top">

`auth_uri`

</td>
<td valign="top">

Base64-encoded Authorization URI from the service account key JSON

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set by default and do not need to be passed in the API request:
> 
> -   `type`: HTTP
> -   `proxyType`: Internet
> -   `tokenServiceURLType`: Dedicated



## Example

```

curl --request POST \
----url $AI_API_URL/v2/admin/secrets
--header 'AI-Resource-Group: <resource group created for grounding>' \
--header 'Authorization: Bearer <Bearer token>' \
--header 'Content-Type: application/json' \
--data-raw '{
  "name": "<GENERIC_SECRET_NAME>",
  "data": {
    "description": "<BASE64_ENCODED_DESCRIPTION>",
    "clientId": "<BASE64_ENCODED_CLIENT_ID>",
    "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=",
    "url": "aHR0cHM6Ly9nb29nbGVhcGlzLmNvbS9kcml2ZS92Mw==",
    "tokenServiceURL": "aHR0cHM6Ly9vYXV0aDIuZ29vZ2xlYXBpcy5jb20vdG9rZW4=",
    "private_key": "<BASE64_ENCODED_PRIVATE_KEY>",
    "client_email": "<BASE64_ENCODED_CLIENT_EMAIL>",
    "auth_uri": "<BASE64_ENCODED_AUTH_URI>"
  },
  "labels": [
    {
      "key": "ext.ai.sap.com/document-grounding",
      "value": "true"
    },
    {
      "key": "ext.ai.sap.com/documentRepositoryType",
      "value": "GoogleDrive"
    }
  ]
}'
        
```



## Next Steps

After creating the generic secret, create a [Create a Document Grounding Pipeline Using the Pipelines API](create-a-document-grounding-pipeline-using-the-pipelines-api-d32b146.md).

