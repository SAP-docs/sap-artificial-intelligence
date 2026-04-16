<!-- copyb8e880a0b7924e16ad808138ee6a26a3 -->

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
    
    `{{pipelineId}}` 
    
    </td>
    <td valign="top">
    
    The ID of the pipeline that you want to start
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `metadataOnly`
    
    </td>
    <td valign="top">
    
    A Boolean value.

    `true` updates the metadata only.

    `false` updates you semantic embeddings by processing the documents in your repository.
    
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
    >     "pipelineId":"{{pipelineId}}",
    > 	"metadataOnly": "<Boolean>"
    >   }' 
    > ```




<a name="copyb8e880a0b7924e16ad808138ee6a26a3__section_rbc_dqw_vfc"/>

## Results

The response includes a response code. Code 202 is a successful response.

