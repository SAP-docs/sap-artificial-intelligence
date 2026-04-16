<!-- loio454abf5fb6f84ccc91d684bacbe4fb75 -->

# Create a Pipeline using a Metadata Configuration



## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   You have created a generic secret. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).
-   You've created a metadata configuration and have noted the metadata configuration ID. For more information, see [Create a Metadata Configuration](create-a-metadata-configuration-51a3fe1.md) and [List Metadata Configurations](list-metadata-configurations-c9f00ae.md).




<a name="loio454abf5fb6f84ccc91d684bacbe4fb75__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines`.


Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
</table>

Include the ID of your metadata configuration in your request. For example:

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: <resource group>' \
>   --header 'Content-Type: application/json' \ 
>   --header 'Authorization: Bearer $TOKEN'
>   --data '{
>     "type": "metadata",
>     "configuration": {
>       "metadataConfigld": "<metadata config id>"
>      }
> }'
> ```

