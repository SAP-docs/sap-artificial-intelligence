<!-- loio693c3c09a49c48c1b48709602583a70b -->

# Get Collections

This endpoint allows you to retrieve a list of all collections associated with a specific resource group.



<a name="loio693c3c09a49c48c1b48709602583a70b__section_h3k_tww_vfc"/>

## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections`

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
</table>

```

curl --request GET \
  --url $AI_API_URL/v2/lm/document-grounding/vector/collections \
  --header 'AI-Resource-Group: {{resource_group}}'
  --header 'Authorization: Bearer {{access_token}}'
```



### Pagination Support

You can use OData-compliant query parameters to manage large result sets:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

$top

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Limits the number of results returned. for example., $top=10 returns 10 results.

</td>
</tr>
<tr>
<td valign="top">

$skip

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Skips a specific number of results. for example, $skip=20 skips the first 20.

</td>
</tr>
<tr>
<td valign="top">

$count

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

If true, includes the total count in the response. If false, includes the total number of records in the response.

</td>
</tr>
</table>

For example:

```
curl --request GET  
--url "$AI_API_URL/v2/lm/document-grounding/vector/collections?$top=10&$skip=20&$count=true"  
--header "AI-Resource-Group: {{resource_group}}"
--header 'Authorization: Bearer {{access_token}}' 
```



<a name="loio693c3c09a49c48c1b48709602583a70b__section_vjm_zxw_vfc"/>

## Results

The response is returned in JSON format, and includes a JSON array of collection objects.

