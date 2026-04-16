<!-- loio3a93b6df878842219b767955b097436a -->

# Delete Documents

This endpoint allows you to bulk delete specific documents using document IDs.



## Procedure

Send a DELETE request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/documents`

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

<id1\>..

</td>
<td valign="top">

The Ids of the documents that you want to delete.

</td>
</tr>
</table>

Include the IDs of the documents that you want to delete in the `ids` field of the data.

 > ### Sample Code:  
> ```
> 
> curl --request DELETE \ 
>   --url $AI_API_URL/v2/lm/document-grounding/vector/documents \
>   --header 'AI-Resource-Group: {{resource_group}}' 
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{
>     "ids": [
>       "<id1>",
>       "<id2>",
>       "<id3>"
>     ]
> }' 
> ```

 

<a name="loio3a93b6df878842219b767955b097436a__result_rbc_dqw_vfc"/>

## Results

The response is returned in JSON format, and includes a response code.

The response codes are:

-   202:

    -   Deleted - document IDs successfully deleted

    -   NotFound – document IDs not found and not deleted

-   400: The specification of the resource was incorrect

-   404: The specification of the resource was incorrect

-   422: There are validation issues with the data


