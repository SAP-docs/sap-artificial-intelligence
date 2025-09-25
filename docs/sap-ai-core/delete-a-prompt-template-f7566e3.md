<!-- loiof7566e322c334901aab8e670a35a9216 -->

# Delete a Prompt Template



<a name="loiof7566e322c334901aab8e670a35a9216__prereq_nbg_w2q_fdc"/>

## Prerequisites

-   You have created a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md).

-   You know the template ID of the prompt template that you want to delete. For more information, see [Get a Prompt Template](get-a-prompt-template-bc8cead.md).




<a name="loiof7566e322c334901aab8e670a35a9216__context_mzy_2wq_fdc"/>

## Context

Delete a specific version of the prompt template, for imperatively managed prompt templates only.

By default, prompt templates are handled on the main-tenant level. To handle them on resource-group level, add the `AI-Resource-Group-Scope` and `AI-Resource-Group` headers to your requests. For example:

```

--header 'AI-Resource-Group-Scope: true'
--header 'AI-Resource-Group: <resource group>'
```

> ### Note:  
> For CaaS users the resource-group-id is extracted automatically, and does not need to be provided in the headers.

> ### Note:  
> CaaS users only have write access to prompt templates on a resource-group level.



<a name="loiof7566e322c334901aab8e670a35a9216__steps_b3t_dwq_fdc"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/lm/promptTemplates/{{promptTemplateId}}` and include the template ID of the prompt you want to delete.

> ### Output Code:  
> ```
> {
>   "message": "Prompt deleted successfully."
> }
> ```

