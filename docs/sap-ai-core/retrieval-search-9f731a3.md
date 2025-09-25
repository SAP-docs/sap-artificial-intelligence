<!-- copy9f731a35c3da46a4a3393bbcd967266a -->

# Retrieval Search



## Context

This endpoint allows you to perform a similarity search between the user query and data repositories, returning relevant chunks that match the query.



## Procedure

1.  You can conduct this search by sending a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/retrieval/search`.

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
    
    <user query\>
    
    </td>
    <td valign="top">
    
    The query that you want to be answered from the vector database
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    dataRepositories
    
    </td>
    <td valign="top">
    
    `'*'` searches through all collections. Alternatively, enter a collection ID to retrieve a chunk from that collection.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    dataRepositoryType
    
    </td>
    <td valign="top">
    
    Supported repository types are `vector` and `help.sap.com`. Data from `help.sap.com` is available for retrieval from the database by default.
    
    </td>
    </tr>
    </table>
    



<a name="copy9f731a35c3da46a4a3393bbcd967266a__section_gjd_qk1_jgc"/>

## Examples



### Example with SAP HANA Vector Store, using all “\*” data resitories

> ### Sample Code:  
> ```
> curl --request POST \  
> --url $AI_API_URL/v2/lm/document-grounding/retrieval/search \  
> --header 'AI-Resource-Group: {{resource_group}}' \    
> --header 'Authorization: Bearer {{access_token}}'
> --data '{
>   "query": "<user query>",  
>   "filters": [
>     {
>       "id": "string",
>       "searchConfiguration": {
>         "maxChunkCount": 1
>       },
>       "dataRepositories": ['*']
>       ],
>       "dataRepositoryType": "vector",
>       "dataRepositoryMetadata": [
>       {
>           "key": "type",
>           "value": [
>             "custom"
>           ]
>         }
>       ],
>       "documentMetadata": [
>         {
>           "key": "url",
>           "value": [
>             "http://hello.com",
>             "123"
>           ]
>         }
>       ],
>       "chunkMetadata": [
>         {
>           "key": "index",
>           "value": [
>             "1"
>           ]
>         }
>       ]
>     }
>   ]
> }'
> 
> 
> ```



### Example with help.sap.com

> ### Sample Code:  
> ```
> curl --request POST \  
> --url $AI_API_URL/v2/lm/document-grounding/retrieval/search \  
> --header 'AI-Resource-Group: {{resource_group}}' \    
> --header 'Authorization: Bearer {{access_token}}'
> --data '{   
> 	"query": "<user-query>",   
> 	"filters": [     
> 		{
> 		"id": "string",
> 		"searchConfiguration": {},
> 		"dataRepositories": ["*"],
> 		"dataRepositoryType": "help.sap.com",
> 		"dataRepositoryMetadata": [],
> 		"documentMetadata": [] 
> 	}'
> }'
> 
> ```



## Results

This endpoint returns a response in JSON format. The response includes relevant chunk identified using the similarity search.

