<!-- copyd20e4218111349eca3f0ff92490c2d23 -->

# List Metadata Configurations

Retrieves a paginated list of all available metadata configurations.



<a name="copyd20e4218111349eca3f0ff92490c2d23__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a GET request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations`.

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
    
    For example: `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations``?top=10&skip=0`


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
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Authorization: Bearer {{access_token}}'
> ```



## Results

Successful responses return code **200** and include details of your**metadata configurations** in JSON format.

> ### Output Code:  
> ```
> {
>   "count": 1,
>   "resources": [
>     {
>       "id": "uuid",
>       "name": "Config Name",
>       "destinationName": "destination",
>       "dataRepositoryType": "MSSharePoint",
>       "includePaths": [
>         "/path"
>       ],
>       "enumerationStatus": "IN_PROGRESS"
>     }
>   ]
> }
> ```

Enumeration status values include:

-   NEW
-   IN\_PROGRESS
-   COMPLETE
-   ERROR

