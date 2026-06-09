<!-- loiof3dd96febef648dea39f2187ba040038 -->

# Metadata



## Context

Metadata is additional informatio, such as tags, categories, or custom attributes that you can add to your collections, documents, or chunks to help organize, filter, and search your content more effectively.

You can update metadata for multiple collections or multiple documents or multiple chunks in a single API request.

You can use the following operations:


<table>
<tr>
<th valign="top">

Operation

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`add`

</td>
<td valign="top">

If the key is present, then it will add the new values.

If the key is absent, it will add the key and the values.

</td>
</tr>
<tr>
<td valign="top">

`remove`

</td>
<td valign="top">

If the key is present, then it will remove the values from it.

</td>
</tr>
<tr>
<td valign="top">

`replace`

</td>
<td valign="top">

If the key is present, it will replace the entire list of values with the new values.

If the key is absent, it will add the key and the values.

</td>
</tr>
<tr>
<td valign="top">

`delete_key`

</td>
<td valign="top">

If the key is present, then it will remove the key and all its values.

</td>
</tr>
</table>



### Limits

The following limits are the maximum number of updates that can be applied in each update:

-   **5** update blocks per **PATCH request**. Ids can be grouped as required.

-   **10** IDs per **update block**.

-   **10** metadata updates per **update block**.

-   For `remove` or `delete_key` operations: **1** operation per **update**.
-   For `add` or `replace` operations: **2** operations per **update**.
-   **10** values per **operation**.




## Procedure

Send a PATCH request to the respective endpoint


<table>
<tr>
<th valign="top">

Resource to be Updated

</th>
<th valign="top">

Endpoint

</th>
</tr>
<tr>
<td valign="top">

Collections

</td>
<td valign="top">

`$AI_API_URL/v2/lm/document-grounding/vector/collections/metadata`

</td>
</tr>
<tr>
<td valign="top">

Documents

</td>
<td valign="top">

`$AI_API_URL/v2/lm/document-grounding/vector/documents/metadata`

</td>
</tr>
<tr>
<td valign="top">

Chunks

</td>
<td valign="top">

`$AI_API_URL/v2/lm/document-grounding/vector/chunks/metadata`

</td>
</tr>
</table>

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`{{resource_group}}`

</td>
<td valign="top">

The AI resource group assigned to your account

</td>
</tr>
<tr>
<td valign="top">

`$AI_API_URL`

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
<tr>
<td valign="top">

`{{access_token}}`

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

`{{resource_id_1}}`

</td>
<td valign="top">

The ID of the collection, document, or chunk that you want to update. You can update multiple resources by providing a list of IDs.

</td>
</tr>
<tr>
<td valign="top">

`{{resource_id_2}}` \(optional\)

</td>
<td valign="top">

The ID of a second collection, document, or chunk that you'd like to update in the same request.

</td>
</tr>
</table>

The sample provided completes the following tasks:

For `{{resource_id_1}}`:

-   If the metadata key `"department"` is not present, the key will be added with values `"finance"` and `"legal"`.

-   If the metadata key `"department"` is present, the values `"finance"` and `"legal"` will be added to the existing values.

-   If the metadata key `"department"` is present, the value `"tech"` will be removed from the existing values.

-   If the metadata key `"status"` exists, the key will be removed.


For `{{resource_id_2}}`:

-   If the metadata key `"department"` is present, all of the values associated with the key will be replaced by the two values `"finance"` and `"legal"`.

-   If the metadata key `"department"` is not present, the key will be added with values `"finance"` and `"legal"`


> ### Sample Code:  
> ```
> curl --request PATCH \  
>  --url $AI_API_URL/v2/lm/document-grounding/vector/collections/metadata \     
>  --header 'AI-Resource-Group: {{resource_group}}' \     
>  --header 'Content-Type: application/json' \  
>  --header 'Authorization: Bearer {{access_token}}' 
>   --data '{ 
>     "updates": [ 
>         { 
>             "ids": [ 
>                 {{resource_id_1}} 
>             ], 
>             "metadataUpdates": [ 
>                 { 
>                     "key": "department", 
>                     "operations": [ 
>                         { 
>                             "op": "add", 
>                             "values": [ 
>                                 "finance", 
>                                 "legal" 
>                             ] 
>                         }, 
>                         { 
>                             "op": "remove", 
>                             "values": [ 
>                                 "tech" 
>                             ] 
>                         } 
>                     ] 
>                 }, 
>                 { 
>                     "key": "status", 
>                     "operations": [ 
>                         { 
>                             "op": "delete_key" 
>                         } 
>                     ] 
>                 } 
>             ] 
>         }, 
>         { 
>             "ids": [ 
>                 {{recource_id_2}} 
>             ], 
>             "metadataUpdates": [ 
>                 { 
>                     "key": "department", 
>                     "operations": [ 
>                         { 
>                             "op": "replace", 
>                             "values": [ 
>                                 "finance", 
>                                 "legal" 
>                             ] 
>                         } 
>                     ] 
>                 } 
>             ] 
>         } 
>     ] 
> }'
> ```



## Results

The response is returned in JSON format, and includes details of the updated resources and metadata.

