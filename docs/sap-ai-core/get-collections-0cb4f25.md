<!-- loio0cb4f2515f31480ba87bc7c8705c7b89 -->

# Get Collections



## Context

Retrieve details of all collections within a specified resource group.



## Procedure

Send a GET request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/collections`

 > ### Sample Code:  
> ```
> 
> curl --request GET \  # Use GET method to retrieve the list of all collections
>   --url $AI_API_URL/v2/lm/document-grounding/vector/collections \  # Endpoint to get all collections
>   --header 'AI-Resource-Group: {{resource_group}}'  # Include the resource group ID in the header
> 
> ```

 