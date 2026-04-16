<!-- loio4fad8fc83cbb43288961e8b2d006e893 -->

# Batch Update Document Metadata

Updates the metadata for multiple documents within a specific metadata configuration in a single request.



## Context

The following limits apply:

-   Maximum 1000 documents per request

-   Maximum 10 metadata entries per document




<a name="loio4fad8fc83cbb43288961e8b2d006e893__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a PATCH request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId>/documents`.

    Include your metadata configuration ID in your request.


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

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

id

</td>
<td valign="top">

The ID of the document to be updated

</td>
</tr>
<tr>
<td valign="top">

labels

</td>
<td valign="top">

Your metadata labels in key-value pairs.

</td>
</tr>
<tr>
<td valign="top">

matchMode

</td>
<td valign="top">

One of the following modes:

-   `ANY`

    -   At least one metadata value matches.

    -   This is the default match mode.

    -   Defined only at injection time.


-   `ALL`

    -   All document metadata values must match exactly, or be a subset of the search metadata.

    -   Supported only at the document level.

    -   Defined only at injection time.





</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl --request PATCH \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId>/documents/<documentId> \
>   --header 'AI-Resource-Group: <resource_group>' \
>   --header 'Content-Type: application/json' \
>   --header 'Authorization: Bearer $TOKEN' \
>   --data '{
>   "value": [
>     {
>       "id": "<documentId>",
>       "metadata": [
>         {
>           "key": "contentObjectId",
>           "value": [
>             "12345"
>           ],
>           "matchMode": "ANY"
>         }
>       ]
>     }
>   ]
> }'
> 
> ```



## Results

Successful responses return code **200** and include details of the document in JSON format.

> ### Output Code:  
> ```
> { 
> "id": "document-uuid", 
> "metadata": [...] 
> } 
> ```

