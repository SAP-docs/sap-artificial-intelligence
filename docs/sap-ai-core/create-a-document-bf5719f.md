<!-- copybf5719f6c2984fa0997b03cef4bf6e90 -->

# Create a Document

This endpoint allows you to add a document with associated metadata and chunks to a collection. Documents are units of text-based content that you upload into a collection, to be used for semantic search and grounding.



<a name="copybf5719f6c2984fa0997b03cef4bf6e90__section_ug1_vfx_vfc"/>

## Prerequisites

You have created a document collection. For more information, see [Vector API](vector-api-08e3d00.md) and [Create a Collection](create-a-collection-c124fb9.md).

You know the ID of the collection that you want to add documents to. For more information, see [Get a Collection](get-a-collection-624cdbb.md).



## Procedure

1.  Send a POST request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents`.

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
    
    Content-Type
    
    </td>
    <td valign="top">
    
    application/json
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \{\{collectionId\}\}
    
    </td>
    <td valign="top">
    
    The ID of the collection
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    metadata <key\> <value\> pair
    
    </td>
    <td valign="top">
    
    Your choice of metadata key value pair
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    chunks
    
    </td>
    <td valign="top">
    
    Text content in chunks
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    metadata <key\> <value\> pair \(chunks\)
    
    </td>
    <td valign="top">
    
    Your choice of metadata key value pair
    
    </td>
    </tr>
    </table>
    
    > ### Sample Code:  
    > ```
    > curl --request POST \ 
    >  --url  $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}}/documents\    
    >  --header 'AI-Resource-Group: {{resource_group}}' \    
    >  --header 'Content-Type: application/json' \ 
    >  --header 'Authorization: Bearer {{access_token}}'
    >   --data '{ 
    >   "documents": [ 
    >     { 
    >       "metadata": [
    >         { 
    >           "key": "url", 
    >           "value": [ 
    >             "http://hello.com", 
    >             "123" 
    >           ] 
    >         } 
    >       ], 
    >       "chunks": [
    >         { 
    >           "content": "<chunk content 1>",
    >           "metadata": [  // 
    >             { 
    >               "key": "index", 
    >               "value": [ 
    >                 "1" 
    >               ] 
    >             } 
    >           ] 
    >         }, 
    >         { 
    >           "content": "<chunk content 2>", 
    >           "metadata": [
    >             { 
    >               "key": "index", 
    >               "value": [ 
    >                 "2" 
    >               ] 
    >             } 
    >           ] 
    >         } 
    >       ] 
    >     } 
    >   ] 
    > }' 
    > ```




<a name="copybf5719f6c2984fa0997b03cef4bf6e90__section_rbc_dqw_vfc"/>

## Results

The response is returned in JSON format, and includes a response code.

The response codes are:

-   201: Created \(successful response\)

-   400: The specification of the resource was incorrect

-   404: The specification of the resource was incorrect

-   422: There are validation issues with the data




<a name="copybf5719f6c2984fa0997b03cef4bf6e90__postreq_jlk_zbz_fgc"/>

## Next Steps

To search for relevant chunks within a specific collection or across all collections based on a user query, use vector search. For more information, see [Vector Search](vector-search-255589a.md).

To search for relevant chunks across all collections based on a user query, use the Retrieval API. For more information, see [Retrieval API](retrieval-api-281e8cf.md).

To use your documents as part of an orchestration workflow, see [Using the Grounding Module](using-the-grounding-module-e1c4dd1.md).

