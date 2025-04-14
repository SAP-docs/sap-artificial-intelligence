<!-- loio45a4f395b22644bf8bca8e89e97df46e -->

# Grounding Generic Secrets for SFTP



<a name="loio45a4f395b22644bf8bca8e89e97df46e__prereq_udx_nph_fdc"/>

## Prerequisites

You have created a resource group for grounding. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-6712bfe.md).



<a name="loio45a4f395b22644bf8bca8e89e97df46e__steps_mm3_sy2_zcc"/>

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

Base64 encoded value in the format `https://<hostname>:<port>` where hostname and port are the SFTP server's hostname and the ports respectively

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

*User* 

</td>
<td valign="top">

Base64 encoded value for SFTP credentials

</td>
</tr>
<tr>
<td valign="top">

*Password* 

</td>
<td valign="top">

Base64 encoded value for SFTP credentials

</td>
</tr>
<tr>
<td valign="top">

*Public Key* 

</td>
<td valign="top">

Base64 encoded value for SFTP public key, which will be used to verify the identity of the SFTP server during the connection setup

</td>
</tr>
<tr>
<td valign="top">

*Public Key Type* 

</td>
<td valign="top">

Base64 encoded value for Base64 encoded value for SFTP public key type: *ssh-ed25519* and *ssh-rsa*.

</td>
</tr>
</table>

> ### Note:  
> The following attributes are hard coded inside `data`, and do not need to be passed during the API call:
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
    "password": "<password>",                            
    "user": <user>,                                      
    "public_key": <public key>,                          
    "public_key_type": <public key type>             
  },
  "labels": [
    {
      "key": "ext.ai.sap.com/document-grounding",         // Label for Document Grounding feature
      "value": "true"
    },
    {
      "key": "ext.ai.sap.com/documentRepositoryType",     // Label for Document Repository Type
      "value": "SFTP"
    }
    }
  ]
}'					
```

**Related Information**  


[Update a Generic Secret](update-a-generic-secret-b5d5970.md "")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "")

