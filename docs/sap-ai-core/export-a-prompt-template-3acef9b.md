<!-- loio3acef9b569184a96bbe19f817cfc3935 -->

# Export a Prompt Template



<a name="loio3acef9b569184a96bbe19f817cfc3935__prereq_nbg_w2q_fdc"/>

## Prerequisites

-   You have created a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md).




## Context

You can export a prompt template as a single file export in declarative compatible yaml format.

By default, prompt templates are handled on the main-tenant level. To handle them on resource-group level, add the `AI-Resource-Group-Scope` and `AI-Resource-Group` headers to your requests. For example:

```

--header 'AI-Resource-Group-Scope: true'
--header 'AI-Resource-Group: <resource group>'
```

> ### Note:  
> For CaaS users the resource-group-id is extracted automatically, and does not need to be provided in the headers.



## Procedure

Send a GET request to the endpoint `{{apiurl}}/v2/lm/promptTemplates/{{promptTemplateId}}/export`, and include the name of your file in the `output` parameter.

 > ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/v2/lm/promptTemplates/{{promptTemplateId}}/export" \
> -Header "Authorization: Bearer <your_auth_token>" \
> --output "exported_prompt_template.yaml"
> ```

 > ### Output Code:  
> ```
> name: example-prompt-template
> version: 0.0.1
> scenario: job-description
> spec:
>     template:
>         - role: 'system'
>         content: 'You classify input text into the two following categories: {{?categories}}'
>         - role: 'user'
>         content: '{{?inputExample}}'
>     defaults:
>         categories: Finance, Tech, Sports
>     additional_fields:
>         modelParams:
>             temperature: 0.7
>             max_tokens: 100
>         modelGroup: chat
>         collection: abc
> ```

