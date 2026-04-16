<!-- copy3be4a11f4dd34bffb755209a3b2cac27 -->

# Retrieve a Specific Data Respository



<a name="copy3be4a11f4dd34bffb755209a3b2cac27__section_xys_lfl_dgc"/>

## Context

This endpoint allows you to retrieve a specific data repository or vector collection stored in the vector database.



## Procedure

1.  You can retrieve a data repository or vector collection by sending a GET request to the endpoint `$AI_API_URL/v2/lm/document-grounding/retrieval/dataRepositories/{{repositoryId}}`.

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
    
    > ### Sample Code:  
    > ```
    > curl --request GET \
    >   --url $AI_API_URL/v2/lm/document-grounding/retrieval/dataRepositories/{{repositoryId}} \
    >   --header 'AI-Resource-Group: {{resource_group}}'
    >   --header 'Authorization: Bearer {{access_token}}'
    > ```




This endpoint returns a response in JSON format. The response includes the specific data repository or vendor collection.

