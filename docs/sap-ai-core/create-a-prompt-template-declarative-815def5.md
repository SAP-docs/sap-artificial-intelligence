<!-- loio815def52a7254a8f8e3e48db41ab57a3 -->

# Create a Prompt Template \(Declarative\)



<a name="loio815def52a7254a8f8e3e48db41ab57a3__prereq_vn5_gs3_fdc"/>

## Prerequisites

-   You've created and synced a git repository. For more information, see [Add a Git Repository](add-a-git-repository-b668176.md).

-   You've created an application that points to the prompt templates in your git repository. For more information, see [Create an Application](create-an-application-80dbecf.md).




<a name="loio815def52a7254a8f8e3e48db41ab57a3__context_xgt_fbp_hdc"/>

## Context

> ### Recommendation:  
> The declarative API utilizes SAP AI Core applications and is recommended for runtime application use cases and CI/CD pipelines. You can manage your prompt templates in a git repository declaratively. Your commits are automatically synchronized with the prompt registry.



<a name="loio815def52a7254a8f8e3e48db41ab57a3__steps_khq_fbq_hdc"/>

## Procedure

Create a prompt template and push it to your git repository. The file name must be in the format `<name>.prompttemplate.ai.sap.yaml` to be recognized.

The following formats are supported:

-   yaml


> ### Sample Code:  
> ```
> name: simple
> version: 0.0.1
> scenario: my-scenario
> spec:
>   template:
>     - role: "system"
>       content: "{{ ?instruction }}"
>     - role: "user"
>       content: "Some more {{ ?user_input }}"
>   defaults:
>     instruction: "default instruction"
>   additionalFields:
>     isDev: true
>     validations:
>       required: true
>     blockedModels:
>       - name: "gpt-4"
>         versions: "gpt-4-vision"
>       - name: "gpt-4o"
>         versions: "*"
> ```

-   The `defaults` and `additionalFields` fields are optional.

-   The `additionalFields` field is unstructured and can be used to store metadata or configuration objects.


Your template syncs automatically. After a few minutes, you'll be able to verify your template by sending a GET request to the endpoint `{{apiurl}}/lm/promptTemplates`.

> ### Sample Code:  
> ```
> 
> {
>     "count": 3,
>     "resources": [
>         {
>             "id": "a460d210-df38-4867-9535-7a556701a4b0",
>             "name": "simple",
>             "version": "0.0.1",
>             "scenario": "my-scenario",
>             "creationTimestamp": "2024-08-18T14:50:17.157000",
>             "managedBy": "declarative",
>             "isVersionHead": true
>         },
>         {...}
>     ]
> }
> ```

The prompt template is marked as `managedBy`: *<declarative\>*. Declarative managed prompt templates are always the head version and can't be edited with the imperative API.



<a name="loio815def52a7254a8f8e3e48db41ab57a3__postreq_dg1_hb3_hdc"/>

## Next Steps

You use your prompt template at runtime. For more information, see [Use a Prompt Template](use-a-prompt-template-ebe1e30.md).

You can change templates locally and push them to git.

> ### Tip:  
> For declaratively managed templates, use the history capabilities in git to track your changes.

