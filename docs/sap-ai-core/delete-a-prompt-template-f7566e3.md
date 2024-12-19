<!-- loiof7566e322c334901aab8e670a35a9216 -->

# Delete a Prompt Template



<a name="loiof7566e322c334901aab8e670a35a9216__prereq_nbg_w2q_fdc"/>

## Prerequisites

-   You have created a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md).

-   You know the template ID of the prompt template that you want to delete. For more information, see [Get a Prompt Template](get-a-prompt-template-bc8cead.md).




<a name="loiof7566e322c334901aab8e670a35a9216__context_mzy_2wq_fdc"/>

## Context

Delete a specific version of the prompt template, for imperatively managed prompt templates only.



<a name="loiof7566e322c334901aab8e670a35a9216__steps_b3t_dwq_fdc"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/lm/promptTemplates/{{promptTemplateId}}` and include the template ID of the prompt you want to delete.

> ### Output Code:  
> ```
> {
>   "message": "Prompt deleted successfully."
> }
> ```

