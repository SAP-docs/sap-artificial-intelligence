<!-- loio8737ceb3ac2b4178aafc84994323b76a -->

# Grounding Generic Secrets for SAP Build Work Zone

Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.



<a name="loio8737ceb3ac2b4178aafc84994323b76a__section_udx_nph_fdc"/>

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




<a name="loio8737ceb3ac2b4178aafc84994323b76a__section_ytf_w5v_c2c"/>

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

Base64 encoded value for your SAP Build Work Zone URL

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
    "url": "< base64 encoded SAP Build Work Zone-server-url>", 
    "clientId": "< base64 encoded client-id>", 
    "clientSecret": "< base64 encoded client-secret>", 
    "tokenServiceURL": "< base64 encoded token-service-url>" 
  }, 
  "labels": [ 
    { 
      "key": "ext.ai.sap.com/document-grounding", 
      "value": "true" 
    }, 
    { 
      "key": "ext.ai.sap.com/documentRepositoryType", 
      "value": "WorkZone" 
    } 
  ] 
}'
```



<a name="loio8737ceb3ac2b4178aafc84994323b76a__section_m4v_r1z_3gc"/>

## Next Steps

After registering your repository with grounding, you can use the document grounding APIs to prepare and store your vectors. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

