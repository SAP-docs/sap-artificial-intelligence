<!-- loio8d022355037643cebf775cd3bf662cc5 -->

# Orchestration

The orchestration service runs on SAP AI Core under the global AI scenario `orchestration`. It provides unified access to multiple generative AI models through consistent code, configuration, and deployment.

Orchestration offers a harmonized API that allows you to use different foundation models without changing the client code. To use different foundation models and versions, you need to create at least one orchestration deployment, or use the orchestration deployment in your default resource group.

Key features of orchestration include:

-   **Templating:** This feature lets you compose prompts with placeholders that are populated during inference.

-   **Content filtering:** This feature allows you to restrict the type of content passed to and received from generative AI models.

-   **Data masking:** This feature enables anonymization or pseudonymization of data before passing it to a generative AI model. With pseudonymization, masked data in the model's response is automatically restored.

-   **Grounding:** This feature lets you integrate external, domain-specific, or real-time data to enhance pretrained models with contextually relevant information beyond their general training material.

-   **Translation:** This feature lets you add translation capabilities for both input and output in your orchestration workflow.


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

> ### Tip:  
> To integrate orchestration into your application, the SAP Cloud SDK for AI is recommended. For more information, see [Libraries and SDKs](libraries-and-sdks-499309d.md).

-   **[Orchestration Workflow V1 \(Deprecated\)](orchestration-workflow-v1-deprecated-b233648.md "In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single
		API call. Within the pipeline, the response from one module is used as the input for the next module.")**  
In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.
-   **[Orchestration Workflow V2](orchestration-workflow-v2-41a0247.md "In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single
		API call. Within the pipeline, the response from one module is used as the input for the next module.")**  
In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.
-   **[Harmonized API](harmonized-api-e99365f.md "The Harmonized API lets you use different foundation models without the need to change
    the client code. It does so by taking the OpenAI API as the standard and mapping other model
    APIs to it. This includes standardizing message formats, model parameters, and response formats.
    The Harmonized API is integrated into the templating module, the model configuration, and the
    orchestration response.")**  
The Harmonized API lets you use different foundation models without the need to change the client code. It does so by taking the OpenAI API as the standard and mapping other model APIs to it. This includes standardizing message formats, model parameters, and response formats. The Harmonized API is integrated into the templating module, the model configuration, and the orchestration response.
-   **[Embeddings](embeddings-67fdf29.md "")**  

-   **[Streaming](streaming-3340907.md "")**  

-   **[Model Restriction](model-restriction-4d499ee.md "")**  

-   **[Structured Output](structured-output-550409d.md "")**  

-   **[Error Handling](error-handling-7597e89.md "")**  

-   **[Orchestration Tutorials](orchestration-tutorials-d051b35.md "Find your use case with orchestration capabilities.")**  
Find your use case with orchestration capabilities.

