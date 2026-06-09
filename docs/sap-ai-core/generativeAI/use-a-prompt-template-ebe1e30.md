<!-- loioebe1e30694ea46269cfe4cdcf1caa5a8 -->

# Use a Prompt Template



<a name="loioebe1e30694ea46269cfe4cdcf1caa5a8__prereq_nbg_w2q_fdc"/>

## Prerequisites

-   You have created a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md).




<a name="loioebe1e30694ea46269cfe4cdcf1caa5a8__context_tdx_xdn_ngc"/>

## Context

By default, prompt templates are handled on the main-tenant level. To handle them on resource-group level, add the `AI-Resource-Group-Scope` and `AI-Resource-Group` headers to your requests. For example:

```

--header 'AI-Resource-Group-Scope: true'
--header 'AI-Resource-Group: <resource group>'
```

> ### Note:  
> For CaaS users, the resource-group-id is extracted automatically, and doesn't need to be provided in the headers.

> ### Note:  
> CaaS users only have write access to prompt templates on a resource-group level.



<a name="loioebe1e30694ea46269cfe4cdcf1caa5a8__steps_h1s_lwh_hdc"/>

## Procedure

You can fill a prompt template by ID, or by the combination of name, scenario, and version.

-   To fill a prompt template by ID, send a POST request to the endpoint `{{apiurl}}/v2/lm/promptTemplates/{{promptTemplateId}}/substitution` and add your variable values in the body.

-   > ### Sample Code:  
    > ```
    > curl -X POST "{{apiurl}}/v2/lm/promptTemplates/{{promptTemplateId}}/substitution" \
    >      -H "Authorization: Bearer <your_auth_token>" \
    >      -H "Content-Type: application/json" \
    >      -d '{
    >            "inputParams": {
    >              "inputExample": "Sample text"
    >            }
    >          }'
    > ```

-   To fill a prompt template by name, scenario, and version send a POST request to the endpoint `{{apiurl}}/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/substitution` and add your variable values in the body.

    > ### Sample Code:  
    > ```
    > curl -X POST "{{apiurl}}/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/substitution" \
    >      -H "Authorization: Bearer <your_auth_token>" \
    >      -H "Content-Type: application/json" \
    >      -d '{
    >            "inputParams": {
    >              "inputExample": "Sample text"
    >            }
    >          }'
    > ```


To return a response containing the full prompt template definition, include the optional query parameter <code><code>metadata</code> = <i class="varname">&lt;true&gt;</i></code>

