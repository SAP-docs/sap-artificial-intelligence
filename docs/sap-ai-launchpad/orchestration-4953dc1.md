<!-- copy4953dc10c6dd48fe85f37b41109dffe2 -->

# Orchestration

The orchestration service operates under the global AI scenario `orchestration`, which is managed by SAP AI Core. This service enables the use of various generative AI models with a unified code, configuration, and deployment.

In this orchestration, the harmonized API allows you to use different foundation models without changing the client code. To use different foundation models and versions, you need to create at least one orchestration deployment, or use the orchestration deployment in your default resource group.

Key features include:

-   **Templating:** This feature lets you compose prompts with placeholders that are filled during inference.

-   **Content filtering:** This feature allows you to restrict the type of content passed to and received from a generative AI model.

-   **Data masking:** This feature enables data masking through anonymization or pseudonymization before passing it into a generative AI model. If pseudonymization is used, masked data in the model's response will be unmasked.

-   **Grounding:** This feature lets you integrate external, contextually relevant, domain-specific, or real-time data into AI processes. This data enhances the natural language processing capabilities of pretrained models, which are trained on general material.

-   **Translation:** This feature lets you integrate translation into your orchestration workflow for both input and output.


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

-   **[Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4344c5b.md "
		
	")**  

-   **[Build Your Orchestration Workflow](build-your-orchestration-workflow-b7dc8b4.md "You build your orchestration workflow by designing and testing a prompt that can be
		populated with different data during inference.")**  
You build your orchestration workflow by designing and testing a prompt that can be populated with different data during inference.
-   **[Test Your Orchestration Workflow](test-your-orchestration-workflow-5b0183d.md "After you have built your orchestration workflow, you can test it to generate output
		from your chosen model.")**  
After you have built your orchestration workflow, you can test it to generate output from your chosen model.

