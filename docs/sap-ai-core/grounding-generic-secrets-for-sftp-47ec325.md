<!-- copy47ec32548c7d439b8b16117817b14e4d -->

# Grounding Generic Secrets for SFTP

Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.



<a name="copy47ec32548c7d439b8b16117817b14e4d__section_udx_nph_fdc"/>

## Prerequisites

You have created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).



## Procedure

1.  Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

    Include the following headers in your request:

    -   `AI_API_URL`: the base URL of your SAP AI Core environment.
    -   `{{access_token}}`: Your access token for SAP AI Core

    Choose one from the following headers to set your scope:

    -   `AI-Tenant-Scope` : `true`. The operation is performed at the main tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-for-grounding-name&gt;</i></code>. The operation is performed at the resource-group level.

    The following API request is used to create a generic secret with base64-encoded values, such as client credentials and other necessary fields, for integrating grounding in the generative AI hub.




<a name="copy47ec32548c7d439b8b16117817b14e4d__section_ytf_w5v_c2c"/>

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

Base64 encoded value in the format `https://<hostname>:<port>` where hostname and port are the SFTP server's hostname and the ports respectively

</td>
</tr>
<tr>
<td valign="top">

`authentication` 

</td>
<td valign="top">

Base64 encoded value for `NoAuthentication` 

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

`user` 

</td>
<td valign="top">

Base64 encoded value for SFTP credentials

</td>
</tr>
<tr>
<td valign="top">

`password` 

</td>
<td valign="top">

Base64 encoded value for SFTP credentials

</td>
</tr>
<tr>
<td valign="top">

`public_key` 

</td>
<td valign="top">

Base64 encoded value for SFTP public key, which will be used to verify the identity of the SFTP server during the connection setup

</td>
</tr>
<tr>
<td valign="top">

`public_key_type` 

</td>
<td valign="top">

Base64 encoded value for SFTP public key type: `ssh-ed25519` and `ssh-rsa`.

</td>
</tr>
</table>

> ### Note:  
> The following attributes are set as default, and do not need to be passed during the API call:
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
    "password": "<password>",                            
    "user": "<user>",                                      
    "public_key": "<public key>",                          
    "public_key_type": "<public key type>"             
  },
  "labels": [
    {
      "key": "ext.ai.sap.com/document-grounding",
      "value": "true"
    },
    {
      "key": "ext.ai.sap.com/documentRepositoryType",
      "value": "SFTP"
    }
    }
  ]
}'
```



<a name="copy47ec32548c7d439b8b16117817b14e4d__section_m4v_r1z_3gc"/>

## Next Steps

After registering your repository with grounding, you can use the document grounding APIs to prepare and store your vectors. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

