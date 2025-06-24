<!-- loio526b0ba358944d03b5454c801e1d8252 -->

# Grounding Generic Secrets for AWS S3



<a name="loio526b0ba358944d03b5454c801e1d8252__prereq_udx_nph_fdc"/>

## Prerequisites

You have created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-6712bfe.md).



<a name="loio526b0ba358944d03b5454c801e1d8252__steps_mm3_sy2_zcc"/>

## Procedure

Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.

In your request, you'll need to specify the resource group you created for grounding purposes, by setting the document grounding label to `true`.

The following API request is used to create a generic secret with base64-encoded values, such as client credentials and other necessary fields, for integrating grounding in the generative AI hub.

<a name="concept_ytf_w5v_c2c"/>

<!-- concept\_ytf\_w5v\_c2c -->

## Example

The `name` attribute is written without hyphens to make it simple to consume as a Unix environment variable later. It is written in capitals as is convention.

You can use `Client Secret` or `Client Certificate` for the authentication with `OAuth2ClientCredentials`.

Common fields are as follows:


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

Base64-encoded value for the description of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

*URL*

</td>
<td valign="top">

Base64 encoded value for MetaData API Server URL

</td>
</tr>
<tr>
<td valign="top">

*Authentication*

</td>
<td valign="top">

Base64-encoded value for `OAuth2ClientCredentials`

</td>
</tr>
<tr>
<td valign="top">

*Client ID* 

</td>
<td valign="top">

Base64-encoded value for client id

</td>
</tr>
</table>

Additional fields specific to client secret are as follows:


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

*Client Secret* 

</td>
<td valign="top">

Base64 encoded value for your Client Secret

</td>
</tr>
<tr>
<td valign="top">

*Token Service URL* 

</td>
<td valign="top">

Base64 encoded value for token service url for client secret based authentication

</td>
</tr>
</table>

Additional fields specific to Client Certificate are as follows:


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

*Certificate Type* 

</td>
<td valign="top">

Base64-encoded value for `P12` or `PEM` 

</td>
</tr>
<tr>
<td valign="top">

*Certificate Content* 

</td>
<td valign="top">

Base64-encoded value for certificate content

</td>
</tr>
<tr>
<td valign="top">

*Certificate Password* 

</td>
<td valign="top">

Base64-encoded value for password of the certificate if set

</td>
</tr>
<tr>
<td valign="top">

*Token Service URL* 

</td>
<td valign="top">

Base64 encoded value for token service url for certificate based authentication

</td>
</tr>
<tr>
<td valign="top">

*Token Service Body Parameters* 

</td>
<td valign="top">

Base64-encoded value for valid JSON object with key-value pair |

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default and do not need to be passed during the API call:
> 
> -   *type*: `"HTTP"`
> -   *proxyType*: `"Internet"`
> -   *tokenServiceURLType*: `"Dedicated"`

**Example with Client Secret**

```
curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--header 'AI-Resource-Group: <resource group created for grounding>' \
--data-raw '{
  "name": "<generic secret name>",                     
  "data": {
    "url": <url>,
    "description": "<description of generic secret>",
    "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=",
    "clientId": "<client id>",
    "clientSecret": "<client secret>",
    "tokenServiceURL": "<token service url for client secret based authentication>",           
  },
  "labels": [
    {
      "key": "ext.ai.sap.com/document-grounding", 
      "value": "true"
    },
    {
      "key": "ext.ai.sap.com/documentRepositoryType", 
      "value": "S3"
    }
  ]
  }'					
```

**Example with Client Certificate**

```
curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--header 'AI-Resource-Group: <resource group created for grounding>' \
--data-raw '{
  "name": "<generic secret name>", 
  "data": {
     "url": <url>,
    "description": "<description of generic secret>",
    "authentication": "T0F1dGgyQ2xpZW50Q3JlZGVudGlhbHM=",
    "clientId": "<client id>",
    "certificateType": "UDEyCg== [P12] / UEVNCg== [PEM]",
    "certificateContent": "<certificate content>",
    "certificatePassword": "<certificate password>",
    "tokenServiceBodyParameters": "<valid json with key-value pairs>",
    "tokenServiceURL": "<token service url for certificate based authentication>",
  },
  "labels": [
    {
      "key": "ext.ai.sap.com/document-grounding", 
      "value": "true"
    },
    {
    "key": "ext.ai.sap.com/documentRepositoryType", 
    "value": "S3"
    }
  ]
  }'
```

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

[Making requests using the REST API](https://docs.aws.amazon.com/AmazonS3/latest/API/RESTAPI.html)

