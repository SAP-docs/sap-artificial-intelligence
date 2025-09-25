<!-- copy49774bb09bd34497922097ba6c9c1b75 -->

# Get Collection Details

This endpoint allows you to retrieve the details of a specific collection using its collection ID.



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}`.

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
> curl --request GET \  
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}} \ 
>   --header 'AI-Resource-Group: {{resource_group}}'
>   --header 'Authorization: Bearer {{access_token}}'  
> ```

 

<a name="copy49774bb09bd34497922097ba6c9c1b75__result_rbc_dqw_vfc"/>

## Results

The response is returned in JSON format, and includes details of your collection.

