<!-- loio508e66f41fbc4709a53c8f4744aa42fa -->

# Create an Orchestration Config \(Declarative\)



<a name="loio508e66f41fbc4709a53c8f4744aa42fa__prereq_vn5_gs3_fdc"/>

## Prerequisites

-   You've created and synced a git repository. For more information, see [Add a Git Repository](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/b6681769f191490f8832d3fbb6794e89.html "You can use your own git repository to version control your SAP AI Core templates. The GitOps onboarding to SAP AI Core instances involves setting up your git repository and synchronizing your content.") :arrow_upper_right:.

-   You've created an application that points to the orchestration configs in your git repository. For more information, see [Create an Application](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/80dbecf3bc224ef5a300ba214de07973.html "") :arrow_upper_right:.




<a name="loio508e66f41fbc4709a53c8f4744aa42fa__context_xgt_fbp_hdc"/>

## Context

> ### Recommendation:  
> The declarative API utilizes SAP AI Core applications and is recommended for runtime application use cases and CI/CD pipelines. You can manage your orchestration configs in a git repository declaratively. Your commits are automatically synchronized with the prompt registry.

> ### Note:  
> Declarative orchestration configs are always handled on the main-tenant level.



<a name="loio508e66f41fbc4709a53c8f4744aa42fa__steps_khq_fbq_hdc"/>

## Procedure

Create a orchestration config and push it to your git repository. The file name must be in the format `<name>.orchestrationconfig.ai.sap.yaml` to be recognized.

The following formats are supported:

-   yaml


> ### Sample Code:  
> ```
> name: simple
> version: 0.0.1
> scenario: my-scenario
> spec:
>   modules:
>     prompt_templating:
>       prompt:
>         template:
>         - role: system
>           content: You are a helpful customer support assistant.
>         - role: user
>           content: "{{?userQuery}}"
>         defaults:
>           userQuery: How can I help you today?
>       model:
>         name: "<model>"
>         params:
>           temperature: 0.7
>           max_tokens: 500
> ```

The `modules` field is required for orchestration configs. You can define additional configurations as needed for your orchestration workflow. For more information, see [Orchestration Workflow V2](orchestration-workflow-v2-41a0247.md).

Your orchestration config syncs automatically. After a few minutes, you'll be able to verify your config by sending a GET request to the endpoint`$AI_API_URL/v2/registry/v2/orchestrationConfigs`.

> ### Sample Code:  
> ```
> {
>   "count": 1,
>   "resources": [
>     {
>       "id": "f47ac10b-58cc-4372-a567-0e02b2c3d479",
>       "name": "test-i342302",
>       "version": "0.0.1",
>       "scenario": "test-i342302-scenario",
>       "creationTimestamp": "2026-02-02T10:00:00.000000",
>       "managedBy": "declarative",
>       "isVersionHead": true
>     }
>   ]
> }
> ```

The orchestration config is marked as `managedBy`: *<declarative\>*. Declaratively managed orchestration configs are always the head version and can't be edited with the imperative API.



<a name="loio508e66f41fbc4709a53c8f4744aa42fa__postreq_dg1_hb3_hdc"/>

## Next Steps

You use your orchestration config at runtime. For more information, see [Use an Orchestration Config in LLM Orchestration](use-an-orchestration-config-in-llm-orchestration-97e4cd2.md).

You can change your templates locally and push them to git.

> ### Tip:  
> For declaratively managed templates, use the history capabilities in git to track your changes.

