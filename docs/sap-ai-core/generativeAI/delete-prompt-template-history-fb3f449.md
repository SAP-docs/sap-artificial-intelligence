<!-- loiofb3f449c95774ac4a9b0d7e2c8fcc051 -->

# Delete Prompt Template History



## Prerequisites

-   You've created a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md).

-   You know the name, scenario, and version of the prompt template whose history you want to delete. For more information, see [Get Prompt Template History](get-prompt-template-history-dc204cf.md).




<a name="loiofb3f449c95774ac4a9b0d7e2c8fcc051__context_mzy_2wq_fdc"/>

## Context

Delete all non-head versions \(history\) of a specific prompt template. The current head version is preserved. For imperatively managed prompt templates only.

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

Send a DELETE request to the endpoint `$AI_API_URL/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history` and include the scenario, name, and version of the prompt template whose history you want to delete.

```
curl -X DELETE "$AI_API_URL/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history" \
  --header "Authorization: Bearer <your_auth_token>"
```



## Results

> ### Output Code:  
> ```
> 
> {
>   "message": "Prompt template history deleted successfully.",
>   "deleted": 3
> }
> ```

