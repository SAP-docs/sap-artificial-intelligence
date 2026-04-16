<!-- copy6bcde5af4d474e47940255b426a54227 -->

# Get a Metadata Configuration by ID

Retrieves the details of a specific metadata configuration by its ID.



<a name="copy6bcde5af4d474e47940255b426a54227__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a GET request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId>`.

    Include the ID of the metadata configuration that you want to retrieve in your path.

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
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations/<metadataConfigId> \
>   --header 'AI-Resource-Group: <resource_group>' \
>   --header 'Authorization: Bearer $TOKEN'
> ```



## Results

Successful responses return code **200** and include details of your metadata configuration in JSON format.

Error responses include **404**: Metadata configuration not found

