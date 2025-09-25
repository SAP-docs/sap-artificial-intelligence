<!-- copy6ae421f2f07e42cfa8b2d8882f5d09d7 -->

# Grounding Generic Secrets for AWS S3

Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.



<a name="copy6ae421f2f07e42cfa8b2d8882f5d09d7__section_udx_nph_fdc"/>

## Context

You have created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).



## Procedure

1.  Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

    -   `AI-Tenant-Scope` : `true`. The operation is performed at the main tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-for-grounding-name&gt;</i></code>. The operation is performed at the resource-group level.

    The following API request is used to create a generic secret with base64-encoded values, such as client credentials and other necessary fields, for integrating grounding in the generative AI hub.




<a name="copy6ae421f2f07e42cfa8b2d8882f5d09d7__section_ytf_w5v_c2c"/>

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

`url` 

</td>
<td valign="top">

Base64-encoded value in the format <code>https://s3.<i class="varname">&lt;region&gt;</i>.amazonaws.com</code> 

</td>
</tr>
<tr>
<td valign="top">

`authentication` 

</td>
<td valign="top">

Base64-encoded value for `NoAuthentication` 

</td>
</tr>
<tr>
<td valign="top">

`description` 

</td>
<td valign="top">

Base64-encoded value for the description of the generic secret to be created

</td>
</tr>
<tr>
<td valign="top">

`access_key_id` 

</td>
<td valign="top">

Base64-encoded value for access key id

</td>
</tr>
<tr>
<td valign="top">

`bucket` 

</td>
<td valign="top">

Base64-encoded value for AWS S3 bucket name

</td>
</tr>
<tr>
<td valign="top">

`host` 

</td>
<td valign="top">

Base64-encoded value for AWS S3 host

</td>
</tr>
<tr>
<td valign="top">

`region` 

</td>
<td valign="top">

Base64-encoded value for AWS S3 region

</td>
</tr>
<tr>
<td valign="top">

`secret_access_key` 

</td>
<td valign="top">

Base64-encoded value for AWS S3 credentials

</td>
</tr>
<tr>
<td valign="top">

`username` 

</td>
<td valign="top">

Base64-encoded value for AWS S3 credentials

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default and do not need to be passed during the API call:
> 
> -   `type`: `"HTTP"`
> -   `proxyType`: `"Internet"`

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



<a name="copy6ae421f2f07e42cfa8b2d8882f5d09d7__section_m4v_r1z_3gc"/>

## Next Steps

After registering your repository with grounding, you can use the document grounding APIs to prepare and store your vectors. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

[Making requests using the REST API](https://docs.aws.amazon.com/AmazonS3/latest/API/RESTAPI.html)

