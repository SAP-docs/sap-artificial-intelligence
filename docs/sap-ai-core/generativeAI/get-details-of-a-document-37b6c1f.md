<!-- loio37b6c1f79ddf4fe1ba1eb40b776ef1fa -->

# Get Details of a Document

Retrieves details of a document associated with a metadata configuration by document ID.



<a name="loio37b6c1f79ddf4fe1ba1eb40b776ef1fa__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a GET request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId>/documents/<documentId>`.

    Include your metadata configuration ID and document ID in your request.


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

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId>/documents/<documentId> \
>   --header 'AI-Resource-Group: <resource_group>' \
>   --header 'Authorization: Bearer $TOKEN'
> ```



## Results

Successful responses return code **200** and include details of the document in JSON format.

> ### Output Code:  
> ```
> {
>   "id": "doc-uuid",
>   "title": "Document Title",
>   "absoluteFilePath": "/folder/file.pdf",
>   "createdTimestamp": "2025-08-28T06:15:30Z",
>   "mimeType": "application/pdf",
>   "fileSizeMb": "1.5",
>   "metadata": []
> }
> ```

Error responses include **404**:Document not found

