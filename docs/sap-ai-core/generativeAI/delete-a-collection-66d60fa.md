<!-- loio66d60faa0a97486ea80bc52a9645389b -->

# Delete a Collection

This endpoint is used to delete a collection using its collection id.



## Procedure

Send a DELETE request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}`

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
</table>

 > ### Sample Code:  
> ```
> 
> curl --request DELETE \
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}} \
>   --header 'AI-Resource-Group: {{resource_group}}'
>   --header 'Authorization: Bearer {{access_token}}'
> ```

 

<a name="loio66d60faa0a97486ea80bc52a9645389b__result_rbc_dqw_vfc"/>

## Results

The response is returned in JSON format, and includes a `location` header that contains the endpoint that can be used to get the status of deletion. Successful requests return a 202 response.

