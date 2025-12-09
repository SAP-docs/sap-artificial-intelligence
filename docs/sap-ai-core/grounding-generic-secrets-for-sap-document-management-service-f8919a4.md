<!-- loiof8919a4c43994141a5581352d94a4666 -->

# Grounding Generic Secrets for SAP Document Management Service



<a name="loiof8919a4c43994141a5581352d94a4666__section_udx_nph_fdc"/>

## Prerequisites

You have created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).



## Procedure

1.  Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

    Include the following headers in your request:

    -   `AI_API_URL`: the base URL of your SAP AI Core environment.
    -   `{{access_token}}`: Your access token for SAP AI Core

    Choose one from the following headers to set your scope:

    -   `AI-Tenant-Scope` : `true`. The operation is performed at the main tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-for-grounding&gt;</i></code>. The operation is performed at the resource-group level.

    The following API request is used to create a generic secret with base64-encoded values, such as client credentials and other necessary fields, for integrating grounding in the generative AI hub. It can use OAuth2ClientCredentials with client secret.




<a name="loiof8919a4c43994141a5581352d94a4666__section_ytf_w5v_c2c"/>

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

Base64 encoded value for your AI Bridge Service URL and repository path. For example, `https://sdm-ai-bridge.cfapps.<region>.hana.ondemand.com/rest/v1/repositories/<repoID>/metadata`.

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
<tr>
<td valign="top">

`pageSize` \(optional\)

</td>
<td valign="top">

If pagination is required, enter a Base64 encoded value of integer from 1 to 500.

> ### Restriction:  
> Pagination and the page size attribute are only supported if you have a metadata server with pagination implemented. For more information, see [Prepare your Metadata API Server](prepare-your-metadata-api-server-23a0741.md).



</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default, and do not need to be passed during the API call:
> 
> -   `type`: `"HTTP"`
> -   `proxyType`: `"Internet"`
> -   `tokenServiceURLType`: `"Dedicated"`

```
 
curl --request POST \ 
  --url $AI_API_URL/v2/admin/secrets \ 
  --header 'ai-resource-group: {{resource_group}}' \ 
  --header 'content-type: application/json' \ 
  --data '{ 
    "name": "<name-of-secret>", 
    "data": { 
    "description": "<any string base64 encoded>", 
    "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=", 
    "url": "<base64 encoded AI Bridge Service URL>", 
    "clientId": "< base64 encoded client-id>", 
    "clientSecret": "< base64 encoded client-secret>", 
    "tokenServiceURL": "< base64 encoded token-service-url>" 
    "pageSize": "<Base64 encoded integer 1-500>"
  }, 
  "labels": [ 
    { 
      "key": "ext.ai.sap.com/document-grounding", 
      "value": "true" 
    }, 
    { 
      "key": "ext.ai.sap.com/documentRepositoryType", 
      "value": "SDM" 
    } 
  ] 
}'
```



<a name="loiof8919a4c43994141a5581352d94a4666__section_m4v_r1z_3gc"/>

## Next Steps

After registering your repository with grounding, you can use the document grounding APIs to prepare and store your vectors. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

[SAP Document Management Service](https://help.sap.com/docs/DOCUMENT_MANAGEMENT/f6e70dd4bffa4b65965b43feed4c9429/72f18b043abd463aba2a680edc897439.html)

