<!-- copyb1403c02a8254ff4bea5cd626978dcd3 -->

# Delete a Document

This endpoint allows you to delete a specific document from a collection using the collection ID and document ID.



## Procedure

Send a DELETE request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents/{{documentId}}`

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
> curl --request DELETE \ 
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents/{{documentId}} \
>   --header 'AI-Resource-Group: {{resource_group}}' 
>   --header 'Authorization: Bearer {{access_token}}'
> ```

 

<a name="copyb1403c02a8254ff4bea5cd626978dcd3__result_rbc_dqw_vfc"/>

## Results

The response is returned in JSON format, and includes a response code.

The response codes are:

-   202: Deleted \(successful response\)

-   400: The specification of the resource was incorrect

-   404: The specification of the resource was incorrect

-   422: There are validation issues with the data


