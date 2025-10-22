<!-- copy56d80e475b06411e97c54fcf0dd0e850 -->

# Grounding Generic Secrets for Microsoft SharePoint

Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.



<a name="copy56d80e475b06411e97c54fcf0dd0e850__section_udx_nph_fdc"/>

## Prerequisites

-   You've prepared your SharePoint integration. For more information, see [Prepare SharePoint Integration with Joule](https://help.sap.com/docs/joule/integrating-joule-with-sap/prepare-sharepoint-integration).

-   You've created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).




## Procedure

1.  Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

    Include the following headers in your request:

    -   `AI_API_URL`: the base URL of your SAP AI Core environment.
    -   `{{access_token}}`: Your access token for SAP AI Core

    Choose one from the following headers to set your scope:

    -   `AI-Tenant-Scope` : `true`. The operation is performed at the main tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-for-grounding-name&gt;</i></code>. The operation is performed at the resource-group level.

    The following API request is used to create a generic secret with base64-encoded values, such as client credentials and other necessary fields, for integrating grounding in the generative AI hub. It can use OAuth2Password or OAuth2ClientCredentials to generate access tokens.

    > ### Note:  
    > In *API permissions*:
    > 
    > -   If you configure access from SAP BTP with `OAuth2Password` authentication, use the permission name `Sites.Read.All` with type `Delegated`
    > -   If you configure access from SAP BTP with `OAuth2ClientCredentials` authentication, use the permission name `Sites.Selected` with type `Application`
    > 
    > For more information, see [Integrating Joule with SAP Solutions: Configure Access from SAP BTP](https://help.sap.com/docs/JOULE/6189c8655c484916bb8eb767126a653a/753bb61132d9436c81d55de3f8cac40e.html).




<a name="copy56d80e475b06411e97c54fcf0dd0e850__section_ytf_w5v_c2c"/>

## Examples



### Example with OAuth2Password:

The `name` attribute is written without hyphens to make it simple to consume as a Unix environment variable later. It's written in capitals as is convention.


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

`description` 

</td>
<td valign="top">

Base64 encoded value for the description of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

`url` 

</td>
<td valign="top">

Base64 encoded value for `https://graph.microsoft.com` 

</td>
</tr>
<tr>
<td valign="top">

`authentication` 

</td>
<td valign="top">

Base64 encoded value for `OAuth2Password` 

</td>
</tr>
<tr>
<td valign="top">

`user` 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint technical user

</td>
</tr>
<tr>
<td valign="top">

`password` 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint password

</td>
</tr>
<tr>
<td valign="top">

`clientId` 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint Application credentials

</td>
</tr>
<tr>
<td valign="top">

`clientSecret` 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint Application credentials

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL` 

</td>
<td valign="top">

Base64 encoded value for <code>https://login.microsoftonline.com/<b>&lt;Microsoft EntraIDtenantidentifier&gt;</b>/oauth2/v2.0/token</code> 

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default, and don't need to be passed during the API call:
> 
> -   `type`: `"HTTP"`
> -   `proxyType`: `"Internet"`
> -   `Scope`: `https://graph.microsoft.com/.default`

```
curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--header 'AI-Resource-Group: <resource group created for grounding>' \
--data-raw '{
  "name": "<generic secret name>",                     
  "data": {                               
    "description": "<description of generic secret>",   
    "clientId": "<client id>",                       
    "authentication": "T0F1dGgyUGFzc3dvcmQ=",      
    "tokenServiceURL": "<token service url>",      
    "password": "<password>",                                               
    "url": "aHR0cHM6Ly9ncmFwaC5taWNyb3NvZnQuY29t",             
    "user": "<user>",                                  
    "clientSecret": "<client secret>",               
  },
  "labels": [
    {
      "key": "ext.ai.sap.com/document-grounding",
      "value": "true"
     },
     {
      "key": "ext.ai.sap.com/documentRepositoryType",     
       "value": "MSSharePoint"
    }
  ]
}'
```



### Example with OAuth2ClientCredentials:

The `name` attribute is written without hyphens to make it simple to consume as a Unix environment variable later. It's written in capitals as is convention.


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

`description` 

</td>
<td valign="top">

Base64 encoded value for the description of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

`url` 

</td>
<td valign="top">

Base64 encoded value for `https://sap.sharepoint.com/sites/<site-name>` 

</td>
</tr>
<tr>
<td valign="top">

`authentication` 

</td>
<td valign="top">

Base64 encoded value for `OAuth2ClientCredentials` 

</td>
</tr>
<tr>
<td valign="top">

`clientId` 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint Application credentials

</td>
</tr>
<tr>
<td valign="top">

`clientSecret` 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint Application credentials

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL` 

</td>
<td valign="top">

Base64 encoded value for <code>https://login.microsoftonline.com/<b>&lt;Microsoft EntraIDtenantidentifier&gt;</b>/oauth2/v2.0/token</code>

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default, and don't need to be passed during the API call:
> 
> -   `type`: `"HTTP"`
> -   `proxyType`: `"Internet"`
> -   `tokenServiceURLType`: `"Dedicated"`
> -   `Scope`: `https://graph.microsoft.com/.default`

> ### Sample Code:  
> ```
> curl --request POST \
> --url $AI_API_URL/v2/admin/secrets \
> --header 'AI-Resource-Group: <resource group created for grounding>' \
> --data-raw '{
>   "name": "<generic secret name>",                     
>   "data": {                                
>     "description": "<description of generic secret>",   
>     "clientId": "<client id>",                        
>     "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=",          
>     "tokenServiceURL": "<token service url>",                                                   
>     "url": "aHR0cHM6Ly9zYXAuc2hhcmVwb2ludC5jb20vc2l0ZXMvPHNpdGUtbmFtZT4=",                                                   
>     "clientSecret": "<client secret>",            
>   },
>    "labels": [
>     {
>       "key": "ext.ai.sap.com/document-grounding",
>         "value": "true"
>      },
>      {
>       "key": "ext.ai.sap.com/documentRepositoryType",     
>       "value": "MSSharePoint"
>     }
>   ]
> }'
> 
> ```



<a name="copy56d80e475b06411e97c54fcf0dd0e850__section_m4v_r1z_3gc"/>

## Next Steps

After registering your repository with grounding, you can use the document grounding APIs to prepare and store your vectors. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

