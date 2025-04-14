<!-- loiocdd4847a8ec74b10b980c87843d80027 -->

# Orchestration

The orchestration service operates under the global AI scenario `orchestration`, which is managed by SAP AI Core. This service enables the use of various generative AI models with a unified code, configuration, and deployment.

In this orchestration, the harmonized API allows you to use different foundation models without changing the client code. To use different foundation models and versions, you need to create at least one orchestration deployment, or use the orchestration deployment in your default resource group.

Key features include:

-   **Templating:** This feature lets you compose prompts with placeholders that are filled during inference.

-   **Content filtering:** This feature allows you to restrict the type of content passed to and received from a generative AI model.

-   **Data masking:** This feature enables data masking through anonymization or pseudonymization before passing it into a generative AI model. If pseudonymization is used, masked data in the model's response will be unmasked.

-   **Grounding:** This feature lets you integrate external, contextually relevant, domain-specific, or real-time data into AI processes. This data enhances the natural language processing capabilities of pretrained models, which are trained on general material.


The following scenarios are available:


<table>
<tr>
<th valign="top">

Global Scenario

</th>
<th valign="top">

Executable ID

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`orchestration`

</td>
<td valign="top">

`orchestration`

</td>
<td valign="top">

Access to orchestration of generative AI models is provided under the global AI scenario `orchestration`, which is managed by SAP AI Core.

</td>
</tr>
</table>

-   **[Orchestration Workflow](orchestration-workflow-b233648.md "In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single
		API call. Within the pipeline, the response from one module is used as the input for the next module.")**  
In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.
-   **[Harmonized API](harmonized-api-e99365f.md "The Harmonized API lets you use different foundation models without the need to change
    the client code. It does so by taking the OpenAI API as the standard and mapping other model
    APIs to it. This includes standardizing message formats, model parameters, and response formats.
    The Harmonized API is integrated into the templating module, the model configuration, and the
    orchestration response.")**  
The Harmonized API lets you use different foundation models without the need to change the client code. It does so by taking the OpenAI API as the standard and mapping other model APIs to it. This includes standardizing message formats, model parameters, and response formats. The Harmonized API is integrated into the templating module, the model configuration, and the orchestration response.
-   **[Streaming](streaming-3340907.md "")**  

-   **[Model Restriction](model-restriction-4d499ee.md "")**  

-   **[Structured Output](structured-output-550409d.md "")**  

-   **[Error Handling](error-handling-7597e89.md "")**  

-   **[Orchestration Tutorials](orchestration-tutorials-d051b35.md "Find your use case with orchestration capabilities.")**  
Find your use case with orchestration capabilities.

