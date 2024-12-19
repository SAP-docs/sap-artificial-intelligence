<!-- loiobdea3576d4ec482dbeeaeff389d140c6 -->

# Create a Generic Secret for AI Data Management



<a name="loiobdea3576d4ec482dbeeaeff389d140c6__prereq_udx_nph_fdc"/>

## Prerequisites

Your have prepared your SharePoint integration. For more information, see [Prepare SharePoint Integration with Joule](https://help.sap.com/docs/joule/integrating-joule-with-sap/prepare-sharepoint-integration).



<a name="loiobdea3576d4ec482dbeeaeff389d140c6__steps_mm3_sy2_zcc"/>

## Procedure

Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.

The following API request is used to create a generic secret with base64 encoded values, such as client credentials and other necessary fields, for integrating grounding in generative AI hub. It uses OAuth2 Password Authentication to generate access tokens.

```
curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--header 'AI-Resource-Group: default' \
--data-raw '{
  "name": "<generic secret name>",                      // Name of the generic secret to be created
  "data": {
    "type": "SFRUUA==",                                 // Base64 encoded value for HTTP protocol
    "description": "<description of generic secret>",   // Base64 encoded description of the secret
    "clientId": "<client id>",                          // Base64 encoded value of client ID
    "authentication": "T0F1dGgyUGFzc3dvcmQ=",           // Base64 encoded value for OAuth2Password authentication
    "tokenServiceURL": "<token service url>",           // Base64 encoded URL for the token service
    "password": "<password>",                           // Password (Base64 encoded)
    "proxyType": "SW50ZXJuZXQ=",                        // Base64 encoded value for Internet as proxy type
    "url": "aHR0cHM6Ly9ncmFwaC5taWNyb3NvZnQuY29t",      // Base64 encoded value for https://graph.microsoft.com
    "tokenServiceURLType": "RGVkaWNhdGVk",              // Base64 encoded value for Dedicated token service URL type
    "user": "<user>",                                   // Base64 encoded value for user
    "clientSecret": "<client secret>",                  // Base64 encoded value for client secret
    "scope": "aHR0cHM6Ly9ncmFwaC5taWNyb3NvZnQuY29tLy5kZWZhdWx0" // Base64 encoded scope for https://graph.microsoft.com/.default
  },
  "labels": [
    {
      "key": "ext.ai.sap.com/document-grounding",       // Label for Document Grounding feature
      "value": "true"
    }
  ]
}'					
```

> ### Note:  
> The secret name is written without hyphens to make it simple to consume as a Unix environment variable later. It is written in capitals as is convention.



<a name="loiobdea3576d4ec482dbeeaeff389d140c6__postreq_q3k_pfk_ddc"/>

## Next Steps

To edit a generic secret, see [Edit a Generic Secret](https://help.sap.com/docs/AI_CORE/52b4adb30e6744709d6226d2b0659dea/1831845910364e97b3a7c6644a9e1f4b.html).

To delete a generic secret, see [Delete a Generic Secret](https://help.sap.com/docs/AI_CORE/52b4adb30e6744709d6226d2b0659dea/d5d5187da4d2483baa6a203f1bcbe33a.html).

