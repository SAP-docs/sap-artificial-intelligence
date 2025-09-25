<!-- loiodade07ed33cf4dd996878e69be61d1a7 -->

# Generic Secrets for Contextualization with Metadata



<a name="loiodade07ed33cf4dd996878e69be61d1a7__section_udx_nph_fdc"/>

## Prerequisites

You have created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).



## Procedure

1.  Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

    -   `AI-Tenant-Scope` : `true`. The operation is performed at the main tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-for-grounding&gt;</i></code>. The operation is performed at the resource-group level.

    The following API request is used to create a generic secret with base64-encoded values, such as client credentials and other necessary fields, for integrating grounding in the generative AI hub. It can use OAuth2ClientCredentials with client secret or client certificate.


The `name` attribute is written without hyphens to make it simple to consume as a Unix environment variable later. It is written in capitals as is convention.

**Common Fields**


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

Base64 encoded value for the metadata API server URL

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

Base64 encoded value for client ID

</td>
</tr>
<tr>
<td valign="top">

`pageSize` \(optional\)

</td>
<td valign="top">

If pagination is required, enter an integer from 1 to 1000.

> ### Restriction:  
> Pagination and the page size attribute are only supported if you have a metadata server with pagination implemented. For more information, see [Prepare your Metadata API Server](prepare-your-metadata-api-server-23a0741.md).



</td>
</tr>
</table>

**With Client Secret**


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

`clientSecret` 

</td>
<td valign="top">

Base64 encoded value for client secret

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL` 

</td>
<td valign="top">

Base64 encoded value for token service URL for client secret based authentication

</td>
</tr>
</table>

**With Client Certificate**


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

`certificateType` 

</td>
<td valign="top">

Base64 encoded value for `P12` or `PEM` 

</td>
</tr>
<tr>
<td valign="top">

`certificateContent` 

</td>
<td valign="top">

Base64 encoded value for certificate content

</td>
</tr>
<tr>
<td valign="top">

`certificatePassword` \(optional\)

</td>
<td valign="top">

Base64 encoded value for password of the certificate if set

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL` 

</td>
<td valign="top">

Base64 encoded value for token service URL for certificate based authentication

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceBodyParameters` \(optional\)

</td>
<td valign="top">

Base64 encoded value for valid JSON object with key-value pair

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default, and do not need to be passed during the API call:
> 
> -   `type`: `"HTTP"`
> -   `proxyType`: `"Internet"`
> -   `tokenServiceURLType`: `"Dedicated"`

<a name="concept_hk2_cgl_5fc"/>

<!-- concept\_hk2\_cgl\_5fc -->

## Examples



<a name="concept_hk2_cgl_5fc__section_v3k_dgl_5fc"/>

## Example with Client Secret:

> ### Sample Code:  
> ```
> curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
> --header "Authorization: Bearer $TOKEN" \
> --header 'Content-Type: application/json' \
> --header 'AI-Resource-Group: <resource group created for grounding>' \
> --data-raw '{
>   "name": "<generic secret name>",
>   "data": {
>     "url": "<url>",
>     "description": "<description of generic secret>",
>     "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=",
>     "clientId": "<client id>",
>     "clientSecret": "<client secret>",
>     "tokenServiceURL": "<token service url for client secret based authentication>",
>   },
>   "labels": [
>     {
>       "key": "ext.ai.sap.com/document-grounding",
>       "value": "true"
>     },
>     {
>       "key": "ext.ai.sap.com/documentRepositoryType",
>       "value": "MetaData"
>     }
>   ]
> }'
> ```



<a name="concept_hk2_cgl_5fc__section_tdb_jyk_fgc"/>

## Example with Client Secret and Pagination:

> ### Sample Code:  
> ```
> curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
> --header "Authorization: Bearer $TOKEN" \
> --header 'Content-Type: application/json' \
> --header 'AI-Resource-Group: <resource group created for grounding>' \
> --data-raw '{
>   "name": "<generic secret name>",
>   "data": {
>     "url": "<url>",
>     "description": "<description of generic secret>",
>     "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=",
>     "clientId": "<client id>",
>     "clientSecret": "<client secret>",
>     "tokenServiceURL": "<token service url for client secret based authentication>",
>     "pageSize": "<integer 1-1000>"
>   },
>   "labels": [
>     {
>       "key": "ext.ai.sap.com/document-grounding",
>       "value": "true"
>     },
>     {
>       "key": "ext.ai.sap.com/documentRepositoryType",
>       "value": "MetaData"
>     }
>   ]
> }'
> ```



<a name="concept_hk2_cgl_5fc__section_upj_2gl_5fc"/>

## Example with Client Certificate:

> ### Sample Code:  
> ```
> curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
> --header "Authorization: Bearer $TOKEN" \
> --header 'Content-Type: application/json' \
> --header 'AI-Resource-Group: <resource group created for grounding>' \
> --data-raw '{
>   "name": "<generic secret name>",
>   "data": {
>     "url": "<url>",
>     "description": "<description of generic secret>",
>     "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=",
>     "clientId": "<client id>",
>     "certificateType": "UDEyCg== [P12] / UEVNCg== [PEM]",
>     "certificateContent": "<certificate content>",
>     "certificatePassword": "<certificate password>",
>     "tokenServiceBodyParameters": "<valid json with key-value pairs>",
>     "tokenServiceURL": "<token service url for certificate based authentication>
>   },
>   "labels": [
>     {
>       "key": "ext.ai.sap.com/document-grounding",
>       "value": "true"
>     },
>     {
>       "key": "ext.ai.sap.com/documentRepositoryType",
>       "value": "MetaData"
>     }
>   ]
> }'
> ```



<a name="concept_hk2_cgl_5fc__section_xcw_kyk_fgc"/>

## Example with Client Certificate and Pagination:

> ### Sample Code:  
> ```
> curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
> --header "Authorization: Bearer $TOKEN" \
> --header 'Content-Type: application/json' \
> --header 'AI-Resource-Group: <resource group created for grounding>' \
> --data-raw '{
>   "name": "<generic secret name>",
>   "data": {
>     "url": "<url>",
>     "description": "<description of generic secret>",
>     "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=",
>     "clientId": "<client id>",
>     "certificateType": "UDEyCg== [P12] / UEVNCg== [PEM]",
>     "certificateContent": "<certificate content>",
>     "certificatePassword": "<certificate password>",
>     "tokenServiceBodyParameters": "<valid json with key-value pairs>",
>     "tokenServiceURL": "<token service url for certificate based authentication>"
>     "pageSize": "<integer 1-1000>"
>   },
>   "labels": [
>     {
>       "key": "ext.ai.sap.com/document-grounding",
>       "value": "true"
>     },
>     {
>       "key": "ext.ai.sap.com/documentRepositoryType",
>       "value": "MetaData"
>     }
>   ]
> }'
> ```

