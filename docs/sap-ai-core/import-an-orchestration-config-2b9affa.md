<!-- loio2b9affa36d0340848f2b181e7b48e230 -->

# Import an Orchestration Config



## Prerequisites

You have created and exported an orchestration config. For more information, see [Create an Orchestration Config](create-an-orchestration-config-2f27317.md) and [Export an Orchestration Config](export-an-orchestration-config-44db4a5.md).



## Context

You can import an orchestration config as a single file export in YAML format.

Orchestration configs are handled at the tenant level and do not require resource group headers.



## Procedure

Send a POST request to the endpoint `{{apiurl}}/v2/registry/v2/orchestrationConfigs/import`, and include the name of your file in the file parameter.

Set the following in the headers:

-   `AI_API_URL`: the base URL of your SAP AI Core environment.
-   `{{access_token}}`: Your access token for SAP AI Core

> ### Sample Code:  
> ```
> curl -X POST "{{apiurl}}/v2/registry/v2/orchestrationConfigs/import" \
>      -H "Authorization: Bearer <your_auth_token>" \
>      -H "Content-Type: multipart/form-data" \
>      -F "file=@/path/to/your/orchestration-config.yaml"
> 
> ```

> ### Output Code:  
> ```
> {
>   "message": "Orchestration config example-orchestration-config for version 0.0.1 imported successfully.",
>   "id": "<orchestrationConfigId>",
>   "name": "example-orchestration-config",
>   "version": "0.0.1",
>   "scenario": "customer-support"
> }
> 
> ```

