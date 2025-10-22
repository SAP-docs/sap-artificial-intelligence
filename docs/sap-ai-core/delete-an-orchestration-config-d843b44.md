<!-- loiod843b4431f2b457388b559a7c4191443 -->

# Delete an Orchestration Config



## Prerequisites

You have created an orchestration config. For more information, see [Create an Orchestration Config](create-an-orchestration-config-2f27317.md).

You know the config ID of the orchestration config that you want to delete. For more information, see [Get Orchestration Configs](get-orchestration-configs-e8310f5.md).



## Context

Delete a specific version of the orchestration config for imperatively managed configurations.

Orchestration configs are handled at the tenant level and do not require resource group headers.



## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/registry/v2/orchestrationConfigs/{{orchestrationConfigId}}` and include the config ID of the orchestration config you want to delete.

Set the following in the headers:

-   `AI_API_URL`: the base URL of your SAP AI Core environment.
-   `{{access_token}}`: Your access token for SAP AI Core

> ### Sample Code:  
> ```
> curl -X DELETE "{{apiurl}}/v2/registry/v2/orchestrationConfigs/{{orchestrationConfigId}}" \
> -H "Authorization: Bearer <your_auth_token>"
> 
> ```

> ### Output Code:  
> ```
> {
>   "message": "Orchestration config deleted successfully."
> }
> ```

