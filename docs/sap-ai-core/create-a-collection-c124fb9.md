<!-- loioc124fb9b68864fa187243ee4edcf213c -->

# Create a Collection

This endpoint allows you to create a new collection. Collections are logical containers used to store and manage embedded documents and their associated chunks.



<a name="loioc124fb9b68864fa187243ee4edcf213c__section_tzh_5tr_kdc"/>

## Prerequisites

You have created a resource group for grounding purposes. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md)



<a name="loioc124fb9b68864fa187243ee4edcf213c__section_ov1_1wr_kdc"/>

## Context

This endpoint allows you to create a new collection for storing documents and their associated chunks.



## Procedure

1.  Send a POST request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections`.

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
    
    <title of the collection\>
    
    </td>
    <td valign="top">
    
    Your choice of title for the collection
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    <embedding-model-name\>
    
    </td>
    <td valign="top">
    
    The name of the embedding model to be used during vectorization
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    metadata.purpose
    
    </td>
    <td valign="top">
    
    Your choice of text about the purpose of the collection
    
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
    </table>
    
    > ### Note:  
    > The`title` and`metadata`fields are optional.

    > ### Sample Code:  
    > ```
    > 
    > curl --request POST \
    >   --url $AI_API_URL/v2/lm/document-grounding/vector/collections \ 
    >   --header 'AI-Resource-Group: {{resource_group}}' \ 
    >   --header 'Authorization: Bearer {{access_token}}'
    >   --data '{
    >   "title": "<title of the collection>",
    >   "embeddingConfig": {
    >     "modelName": "<embedding-model-name>"
    >   },
    >   "metadata": [
    >     {
    >       "key": "purpose",
    >       "value": [
    >         "<text>"
    >       ]
    >     },
    >     {
    >       "key": "<a-random-key>",
    >       "value": [
    >         "<text>"
    >       ]
    >     }
    >   ]
    > }'
    > ```




<a name="loioc124fb9b68864fa187243ee4edcf213c__section_rbc_dqw_vfc"/>

## Results

The response is returned in JSON format, and includes a `location` header that contains the endpoint that can be used to get the status of collection creation.



<a name="loioc124fb9b68864fa187243ee4edcf213c__postreq_wm5_11z_fgc"/>

## Next Steps

Check the status of your collection. For more information, see [Get Collection Creation Status](get-collection-creation-status-3bbaff2.md).

