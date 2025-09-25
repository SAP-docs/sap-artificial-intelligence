<!-- copy62d73913e7604f739c3aa99176523438 -->

# Update a Document

This endpoint allows you to update an existing document within a collection, including its associated metadata and chunks.



## Procedure

Send a PATCH request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents`

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

Content-Type

</td>
<td valign="top">

application/json

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
<tr>
<td valign="top">

metadata <key\> <value\> pair

</td>
<td valign="top">

Your choice of metadata key value pair

</td>
</tr>
<tr>
<td valign="top">

chunks

</td>
<td valign="top">

Text content in chunks

</td>
</tr>
<tr>
<td valign="top">

metadata <key\> <value\> pair \(chunks\)

</td>
<td valign="top">

Your choice of metadata key value pair

</td>
</tr>
</table>

 > ### Sample Code:  
> ```
> 
> curl --request PATCH \ 
>  --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents \    
>  --header 'AI-Resource-Group: {{resource_group}}' \    
>  --header 'Content-Type: application/json' \ 
>  --header 'Authorization: Bearer {{access_token}}'
>   --data '{ 
>   "documents": [ 
>     { 
>       "id": {{documentId}},
>       "metadata": [
>         { 
>           "key": "url", 
>           "value": [ 
>             "http://hello.com", 
>             "123" 
>           ] 
>         } 
>       ], 
>       "chunks": [
>         { 
>           "content": "<This is an updated document chunk content>", 
>           "metadata": [
>             { 
>               "key": "index", 
>               "value": [ 
>                 "1" 
>               ] 
>             } 
>           ] 
>         } 
>       ] 
>     } 
>   ] 
> }' 
> ```

 

<a name="copy62d73913e7604f739c3aa99176523438__result_rbc_dqw_vfc"/>

## Results

The response is returned in JSON format, and includes a response code.

The reponse codes are:

-   200: OK \(successful response\)

-   400: The specification of the resource was incorrect

-   404: The specification of the resource was incorrect

-   422: There are validation issues with the data


