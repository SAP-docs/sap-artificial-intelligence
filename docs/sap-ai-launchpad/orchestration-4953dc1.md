<!-- copy4953dc10c6dd48fe85f37b41109dffe2 -->

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

-   **[Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4344c5b.md "
		
	")**  

-   **[Build Your Orchestration Workflow](build-your-orchestration-workflow-b7dc8b4.md "You build your orchestration workflow by designing and testing a prompt that can be
		populated with different data during inference.")**  
You build your orchestration workflow by designing and testing a prompt that can be populated with different data during inference.
-   **[Test Your Orchestration Workflow](test-your-orchestration-workflow-5b0183d.md "After you have built your orchestration workflow, you can test it to generate output
		from your chosen model.")**  
After you have built your orchestration workflow, you can test it to generate output from your chosen model.

