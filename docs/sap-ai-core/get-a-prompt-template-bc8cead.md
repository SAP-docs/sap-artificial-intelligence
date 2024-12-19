<!-- loiobc8ceadd9e08423586994b1e30f0d117 -->

# Get a Prompt Template



<a name="loiobc8ceadd9e08423586994b1e30f0d117__prereq_nbg_w2q_fdc"/>

## Prerequisites

-   You have created a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md) and [Create a Prompt Template \(Declarative\)](create-a-prompt-template-declarative-815def5.md).




## Context

You can retrieve a prompt template by ID, or by the combination of name, scenario, and version.

Prompt templates can also be retrieved and consumed in orchestration. For more information, see [Templating](templating-88c5608.md).

> ### Note:  
> Retrieval by ID offers immutability; guaranteeing that the prompt template behind the ID will not change.
> 
> Retrieval by name, scenario, and version are not immutable, and the latest iteration of the prompt template is retrieved.



## Procedure

Send a GET request to the endpoint `{{apiurl}}/lm/promptTemplates`, and include the information for your chosen retrieval method.

> ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/lm/promptTemplates?name=example-prompt-template&scenario=categorization&version=0.0.1" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```

> ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/lm/promptTemplates/{{promptTemplateId}}" \
> -Header "Authorization: Bearer <your_auth_token>"
> ```

