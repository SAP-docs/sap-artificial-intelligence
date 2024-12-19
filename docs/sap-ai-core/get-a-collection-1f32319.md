<!-- loio1f32319380104480ba74f470c25148e8 -->

# Get a Collection



## Context

Retrieve details of a specific collection within a specified resource group.



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections`

 > ### Sample Code:  
> ```
> 
> curl --request GET \  
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections/{{collectionId}} \  # URL to fetch a collection using collectionId
>   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> 
> ```

 