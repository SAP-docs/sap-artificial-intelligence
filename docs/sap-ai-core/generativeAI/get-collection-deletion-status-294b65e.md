<!-- copy294b65ecee1248528a1fb0831ee87a1c -->

# Get Collection Deletion Status

This endpoint allows you to retrieve the status of a collection deletion using the collection ID.



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{id}}/deletionStatus`

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

\{\{id\}\}

</td>
<td valign="top">

The ID of the collection

</td>
</tr>
</table>

 > ### Sample Code:  
> ```
> curl --request GET \  
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{id}}/deletionStatus \
>   --header 'AI-Resource-Group: {{resource_group}}' 
>   --header 'Authorization: Bearer {{access_token}}'
> ```

 

<a name="copy294b65ecee1248528a1fb0831ee87a1c__result_rbc_dqw_vfc"/>

## Results

The response is returned in JSON format, and includes a the status of your collection deletion.

