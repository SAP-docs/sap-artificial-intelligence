<!-- loio932f2b7136e04ae9868783f02acc6ecd -->

# Manually Restart a Document Grounding Pipeline

This endpoint allows you to retrain an existing pipeline manually.



## Context

You can start an existing pipeline by sending a POST request to the endpoint: `/v2/lm/document-grounding/pipelines/trigger` and including your pipeline ID in your request.



## Procedure

1.  Populate the sample code with the following values:


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
    
    \{\{pipelineId\}\}
    
    </td>
    <td valign="top">
    
    The ID of the pipeline that you want to start
    
    </td>
    </tr>
    </table>
    
    > ### Sample Code:  
    > ```
    >  
    > curl --request POST \ 
    >   --url $AI_API_URL/v2/lm/document-grounding/pipelines/trigger \ 
    >   --header 'ai-resource-group: {{resource_group}}' \ 
    >   --header 'Authorization: Bearer {{access_token}}'
    >   --header 'content-type: application/json' \ 
    >   --data '{ 
    >     "pipelineId":"{{pipelineId}}" 
    >   }' 
    > ```




<a name="loio932f2b7136e04ae9868783f02acc6ecd__section_rbc_dqw_vfc"/>

## Results

The response includes a response code. Code 202 is a successful response.

