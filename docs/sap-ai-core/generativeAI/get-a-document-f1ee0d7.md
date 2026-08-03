<!-- copyf1ee0d7bcc344c5788462c3b3007cabb -->

# Get A Document

This endpoint allows you to retrieve a specific document from a collection using the collection ID and document ID.



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents/{{documentId}}`

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

\{\{resource\_group\}\}

</td>
<td valign="top">

The AI resource group assigned to your account

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
<tr>
<td valign="top">

\{\{access\_token\}\}

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

\{\{collectionId\}\}

</td>
<td valign="top">

The ID of the collection

</td>
</tr>
<tr>
<td valign="top">

\{\{documentId\}\}

</td>
<td valign="top">

The ID of the document

</td>
</tr>
</table>

 > ### Sample Code:  
> ```
> 
> curl --request GET \ 
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents/{{documentId}} \
>   --header 'AI-Resource-Group: {{resource_group}}'
>   --header 'Authorization: Bearer {{access_token}}'
> ```

 

<a name="copyf1ee0d7bcc344c5788462c3b3007cabb__result_x1n_pnx_vfc"/>

## Results

The response is returned in JSON format, and includes details of your document.

