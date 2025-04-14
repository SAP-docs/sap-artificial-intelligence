<!-- loio97779dbf118c42e2af617857392349e5 -->

# Generic Secrets for Contextualization



<a name="loio97779dbf118c42e2af617857392349e5__prereq_udx_nph_fdc"/>

## Prerequisites

You have created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-6712bfe.md).



<a name="loio97779dbf118c42e2af617857392349e5__steps_mm3_sy2_zcc"/>

## Procedure

Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.

In your request, you'll need to specify the resource group you created for grounding purposes, by setting the document grounding label to `true`.

The following API request is used to create a generic secret with base64-encoded values, such as client credentials and other necessary fields, for integrating grounding in the generative AI hub. It can use OAuth2ClientCredentials to generate access tokens.

<a name="concept_ytf_w5v_c2c"/>

<!-- concept\_ytf\_w5v\_c2c -->

## Example

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

Base64 encoded value for the metadata api server url

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

*Token Service URL* 

</td>
<td valign="top">

Base64 encoded URL for the token service of metadata api server

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
> --header "Authorization: Bearer $TOKEN" \
> --header 'Content-Type: application/json' \
> --header 'AI-Tenant-Scope: true' \
> --header 'AI-Resource-Group: <resource group created for grounding>' \
> --data-raw '{
>   "name": "<generic secret name>",                        
>   "data": {
>     "url": <url>,                                         
>     "description": "<description of generic secret>",    
>     "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=", 
>     "clientId": "<client id>",                            
>     "clientSecret": "<client secret>",                   
>     "tokenServiceURL": "<token service url>"   
>   },
>   "labels": [
>     {
>       "key": "ext.ai.sap.com/document-grounding",         // Label for Document Grounding feature
>       "value": "true"
>     },
>     {
>       "key": "ext.ai.sap.com/documentRepositoryType",     // Label for Document Repository Type
>       "value": "MetaData"
>     }
>   ]
> }'
> 
> ```

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

