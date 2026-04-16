<!-- loio3cc2e3acf87c4480a4b2c928941a330f -->

# List the Documents of a Metadata Configuration

Retrieves a paginated list of documents associated with a metadata configuration.



<a name="loio3cc2e3acf87c4480a4b2c928941a330f__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a GET request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId>/documents`.

    You can include optional parameters for pagination support. The following query parameters are supported:


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
    
    `absolutePath` 
    
    </td>
    <td valign="top">
    
    String
    
    </td>
    <td valign="top">
    
    The file path to restrict the search to. Wildcards are supported.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `$top` 
    
    </td>
    <td valign="top">
    
    Integer
    
    </td>
    <td valign="top">
    
    Max number of documents to return.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `$skip` 
    
    </td>
    <td valign="top">
    
    Integer
    
    </td>
    <td valign="top">
    
    Number of documents to skip.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `$count` 
    
    </td>
    <td valign="top">
    
    Boolean
    
    </td>
    <td valign="top">
    
    `true`: returns the total number of documents available on the server in the `documentsCount` field.

    `false`: returns the number of documents included in the current response in the `documentsCount` field.
    
    </td>
    </tr>
    </table>
    
    For example: `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId>/documents``?top=10&skip=0`


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
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId>/documents \
>   --header 'AI-Resource-Group: <resource_group>' \
>   --header 'Authorization: Bearer $TOKEN'
> ```



## Results

Successful responses return code **200** and include details of the documents associated with your metadata configurations in JSON format.

> ### Output Code:  
> ```
> {
>   "count": 1,
>   "resources": [
>     {
>       "id": "doc-uuid",
>       "title": "Document Title",
>       "absoluteFilePath": "/folder/file.pdf",
>       "createdTimestamp": "2025-08-28T06:15:30Z",
>       "type": "DOCUMENT",
>       "metadata": []
>     }
>   ]
> }
> ```

Type values include:

-   FOLDER
-   DOCUMENT

