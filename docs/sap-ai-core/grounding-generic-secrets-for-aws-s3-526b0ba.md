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

*URL*

</td>
<td valign="top">

Base64 encoded value in the format <code>https://s3-<i class="varname">&lt;region&gt;</i>.amazonaws.com</code>

</td>
</tr>
<tr>
<td valign="top">

*Authentication*

</td>
<td valign="top">

Base64 encoded value for `NoAuthentication`

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

*Access Key ID* 

</td>
<td valign="top">

Base64 encoded value for access key id

</td>
</tr>
<tr>
<td valign="top">

*Bucket* 

</td>
<td valign="top">

Base64 encoded value for AWS S3 bucket name

</td>
</tr>
<tr>
<td valign="top">

*Host* 

</td>
<td valign="top">

Base64 encoded value for AWS S3 host

</td>
</tr>
<tr>
<td valign="top">

*Region* 

</td>
<td valign="top">

Base64 encoded value for AWS S3 region

</td>
</tr>
<tr>
<td valign="top">

*Secret Access Key* 

</td>
<td valign="top">

Base64 encoded value for AWS S3 credentials

</td>
</tr>
<tr>
<td valign="top">

*Username* 

</td>
<td valign="top">

Base64 encoded value for AWS S3 credentials

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default and do not need to be passed during the API call:
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
    "url": "<url>",                                       
    "authentication": "Tm9BdXRoZW50aWNhdGlvbg==",          
    "description": "<description of generic secret>",    
    "access_key_id": "<access key id>",                 
    "bucket": "<bucket>",                               
    "host": "<host>",                                    
    "region": "<region>",                                
    "secret_access_key": "<secret access key>",          
    "username": "<username>"                           
  },
  "labels": [
    {
      "key": "ext.ai.sap.com/document-grounding",         // Label for Document Grounding feature
      "value": "true"
    },
    {
      "key": "ext.ai.sap.com/documentRepositoryType",     // Label for Document Repository Type
      "value": "S3"
    }
  ]
}'					
```

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

