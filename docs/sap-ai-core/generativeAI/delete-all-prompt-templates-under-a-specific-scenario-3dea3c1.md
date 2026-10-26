<!-- loio3dea3c16dec347db9382aed5b16320e8 -->

# Delete All Prompt Templates under a specific Scenario



## Prerequisites

-   You have created a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md).

-   You know the scenario ID of the scenario whose prompt templates you want to delete.




<a name="loio3dea3c16dec347db9382aed5b16320e8__context_mzy_2wq_fdc"/>

## Context

Delete all prompt templates under a given scenario. This operation affects imperatively managed prompt templates only.

By default, prompt templates are handled on the main-tenant level. To handle them on resource-group level, add the `AI-Resource-Group-Scope` and `AI-Resource-Group` headers to your requests. For example:

```

--header 'AI-Resource-Group-Scope: true'
--header 'AI-Resource-Group: <resource group>'
```

> ### Note:  
> For CaaS users, the resource-group-id is extracted automatically, and doesn't need to be provided in the headers.

> ### Note:  
> CaaS users only have write access to prompt templates on a resource-group level.



## Procedure

Send a DELETE request to the endpoint `$AI_API_URL/v2/lm/scenarios/{{scenarioId}}/promptTemplates` and include the scenario ID.

```
curl -X DELETE "$AI_API_URL/v2/lm/scenarios/{{scenarioId}}/promptTemplates" \
  --header "Authorization: Bearer <your_auth_token>"
```



## Results

> ### Output Code:  
> ```
> {
>   "message": "Prompt templates deleted successfully.",
>   "deleted": 5
> }
> ```

