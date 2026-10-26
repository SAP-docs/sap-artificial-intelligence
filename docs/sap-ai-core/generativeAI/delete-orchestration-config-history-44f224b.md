<!-- loio44f224b5dd854390b4c38f617c9fa952 -->

# Delete Orchestration Config History



## Prerequisites

-   You have created an orchestration config. For more information, see [Create an Orchestration Config \(Imperative\)](create-an-orchestration-config-imperative-2f27317.md).

-   You know the name, scenario, and version of the orchestration config whose history you want to delete. For more information, see [Get Orchestration Config History](get-orchestration-config-history-743e913.md).




<a name="loio44f224b5dd854390b4c38f617c9fa952__context_mzy_2wq_fdc"/>

## Context

Delete all non-head versions \(history\) of a specific orchestration config identified by its scenario, name, and version. The current head version is preserved. For imperatively managed orchestration configs only.

Orchestration configs are handled at the tenant level and do not require resource group headers.



## Procedure

Send a DELETE request to the endpoint `$AI_API_URL/v2/registry/v2/scenarios/{{scenarioId}}/orchestrationConfigs/{{orchestrationConfigName}}/versions/{{versionId}}/history` and include the scenario, name, and version of the orchestration config whose history you want to delete.

```
curl -X DELETE "$AI_API_URL/v2/registry/v2/scenarios/{{scenarioId}}/orchestrationConfigs/{{orchestrationConfigName}}/versions/{{versionId}}/history" \
  --header "Authorization: Bearer <your_auth_token>"
```



## Results

> ### Output Code:  
> ```
> 
> {
>   "message": "Orchestration config history deleted successfully.",
>   "deleted": 3
> }
> ```

