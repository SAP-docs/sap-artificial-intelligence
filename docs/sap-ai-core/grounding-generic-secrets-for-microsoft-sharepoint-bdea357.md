<!-- loiobdea3576d4ec482dbeeaeff389d140c6 -->

# Grounding Generic Secrets for Microsoft SharePoint



<a name="loiobdea3576d4ec482dbeeaeff389d140c6__prereq_udx_nph_fdc"/>

## Prerequisites

You have prepared your SharePoint integration. For more information, see [Prepare SharePoint Integration with Joule](https://help.sap.com/docs/joule/integrating-joule-with-sap/prepare-sharepoint-integration).

You have created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-6712bfe.md).



<a name="loiobdea3576d4ec482dbeeaeff389d140c6__steps_mm3_sy2_zcc"/>

## Procedure

Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.

In your request, you'll need to specify the resource group you created for grounding purposes, by setting the document grounding label to `true`.

The following API request is used to create a generic secret with base64-encoded values, such as client credentials and other necessary fields, for integrating grounding in the generative AI hub. It can use OAuth2Password or OAuth2ClientCredentials to generate access tokens.

> ### Note:  
> In *API permissions*:
> 
> -   If you configure access from SAP BTP with `OAuth2Password` authentication, use the permission name `Sites.Read.All` with type `Delegated`
> -   If you configure access from SAP BTP with `OAuth2ClientCredentials` authentication, use the permission name `Sites.Selected` with type `Application`
> 
> For more information, see [Integrating Joule with SAP Solutions: Configure Access from SAP BTP](https://help.sap.com/docs/JOULE/6189c8655c484916bb8eb767126a653a/753bb61132d9436c81d55de3f8cac40e.html).

<a name="concept_ytf_w5v_c2c"/>

<!-- concept\_ytf\_w5v\_c2c -->

## Examples



<a name="concept_ytf_w5v_c2c__section_ksx_y5v_c2c"/>

## Example with OAuth2Password:

The `name` attribute is written without hyphens to make it simple to consume as a Unix environment variable later. It is written in capitals as is convention.


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

*Name* 

</td>
<td valign="top">

Name of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

*Description* 

</td>
<td valign="top">

Base64 encoded value for the description of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

*URL* 

</td>
<td valign="top">

Base64 encoded value for `https://graph.microsoft.com` 

</td>
</tr>
<tr>
<td valign="top">

*Authentication* 

</td>
<td valign="top">

Base64 encoded value for `OAuth2Password` 

</td>
</tr>
<tr>
<td valign="top">

*User* 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint technical user

</td>
</tr>
<tr>
<td valign="top">

*Password* 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint password

</td>
</tr>
<tr>
<td valign="top">

*Client ID* 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint Application credentials

</td>
</tr>
<tr>
<td valign="top">

*Client Secret* 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint Application credentials

</td>
</tr>
<tr>
<td valign="top">

*Scope* 

</td>
<td valign="top">

Base64 encoded value for `https://graph.microsoft.com/.default` 

</td>
</tr>
<tr>
<td valign="top">

*Token Service URL* 

</td>
<td valign="top">

Base64 encoded value for `https://login.microsoftonline.com/<tenant-id>/oauth2/v2.0/token` 

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default, and do not need to be passed during the API call:
> 
> -   *type*: `"HTTP"`
> -   *proxyType*: `"Internet"`

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
    "scope": "aHR0cHM6Ly9ncmFwaC5taWNyb3NvZnQuY29tLy5kZWZhdWx0" 
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



<a name="concept_ytf_w5v_c2c__section_esl_bvv_c2c"/>

## Example with OAuth2ClientCredentials:

The `name` attribute is written without hyphens to make it simple to consume as a Unix environment variable later. It is written in capitals as is convention.


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

*Name* 

</td>
<td valign="top">

Name of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

*Description* 

</td>
<td valign="top">

Base64 encoded value for the description of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

*URL* 

</td>
<td valign="top">

Base64 encoded value for `https://sap.sharepoint.com/sites/<site-name>` 

</td>
</tr>
<tr>
<td valign="top">

*Authentication* 

</td>
<td valign="top">

Base64 encoded value for `OAuth2ClientCredentials` 

</td>
</tr>
<tr>
<td valign="top">

*Client ID* 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint Application credentials

</td>
</tr>
<tr>
<td valign="top">

*Client Secret* 

</td>
<td valign="top">

Base64 encoded value for your Microsoft SharePoint Application credentials

</td>
</tr>
<tr>
<td valign="top">

*Scope* 

</td>
<td valign="top">

Base64 encoded value for `https://graph.microsoft.com/.default` 

</td>
</tr>
<tr>
<td valign="top">

*Token Service URL* 

</td>
<td valign="top">

Base64 encoded value for `https://login.microsoftonline.com/<tenant-id>/oauth2/v2.0/token`

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default, and do not need to be passed during the API call:
> 
> -   *type*: `"HTTP"`
> -   *proxyType*: `"Internet"`
> -   *tokenServiceURLType*: `"Dedicated"`

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
>     "tokenServiceURLType": "RGVkaWNhdGVk",                                                
>     "url": "aHR0cHM6Ly9zYXAuc2hhcmVwb2ludC5jb20vc2l0ZXMvPHNpdGUtbmFtZT4=",                                                   
>     "clientSecret": "<client secret>",            
>     "scope": "aHR0cHM6Ly9ncmFwaC5taWNyb3NvZnQuY29tLy5kZWZhdWx0" 
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

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

