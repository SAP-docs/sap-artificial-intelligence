<!-- loio6c566dd77a6340c0b7b1cb3bbe4ab42f -->

# Delete All Orchestration Configs under a specific Scenario



## Prerequisites

-   You have created an orchestration config. For more information, see [Create an Orchestration Config \(Imperative\)](create-an-orchestration-config-imperative-2f27317.md).

-   You know the scenario ID of the scenario whose orchestration configs you want to delete.




<a name="loio6c566dd77a6340c0b7b1cb3bbe4ab42f__context_mzy_2wq_fdc"/>

## Context

Delete all orchestration configs under a given scenario. This operation affects imperatively managed orchestration configs only.

Orchestration configs are handled at the tenant level and do not require resource group headers.



## Procedure

Send a DELETE request to the endpoint `$AI_API_URL/v2/registry/v2/scenarios/{{scenarioId}}/orchestrationConfigs` and include the scenario ID.

```
curl -X DELETE "$AI_API_URL/v2/registry/v2/scenarios/{{scenarioId}}/orchestrationConfigs" \
  --header "Authorization: Bearer <your_auth_token>"
```



## Results

> ### Output Code:  
> ```
> {
>   "message": "Orchestration configs deleted successfully.",
>   "deleted": 5
> }
> ```

