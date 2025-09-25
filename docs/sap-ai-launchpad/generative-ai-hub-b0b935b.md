<!-- loiob0b935b86cc944e2875ba01321ff3fc6 -->

# Generative AI Hub

The generative AI hub incorporates generative AI into your AI activities in SAP AI Core and SAP AI Launchpad.



<a name="loiob0b935b86cc944e2875ba01321ff3fc6__section_k14_k3y_bzb"/>

## Scenarios

Access to generative AI models is provided under the global AI scenarios `foundation-models` and `orchestration`. These scenarios are managed by SAP AI Core. Individual models are provided as executables in the form of serving templates, and accessed by choosing the corresponding template for the desired model.

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

foundation-models

</td>
<td valign="top">

azure-openai

</td>
<td valign="top">

The Azure OpenAI Service provides REST API access to OpenAI's LLMs.

</td>
</tr>
<tr>
<td valign="top">

foundation-models

</td>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

Open-source models hosted and accessed through SAP AI Core.

</td>
</tr>
<tr>
<td valign="top">

foundation-models

</td>
<td valign="top">

gcp-vertexai

</td>
<td valign="top">

GCP Vertex AI provides access to PaLM 2 and Gemini models from Google.

</td>
</tr>
<tr>
<td valign="top">

foundation-models

</td>
<td valign="top">

aws-bedrock

</td>
<td valign="top">

AWS Bedrock provides access to foundation models from Anthropic, Amazon, and other providers.

</td>
</tr>
<tr>
<td valign="top">

foundation-models

</td>
<td valign="top">

aicore-mistralai

</td>
<td valign="top">

Models from Mistral AI hosted and accessed through SAP AI Core.

</td>
</tr>
<tr>
<td valign="top">

foundation-models

</td>
<td valign="top">

aicore-ibm

</td>
<td valign="top">

Models from IBM hosted and accessed through SAP AI Core.

</td>
</tr>
<tr>
<td valign="top">

orchestration

</td>
<td valign="top">

orchestration

</td>
<td valign="top">

Access to orchestration of generative AI models is provided under the global AI scenario `orchestration`, which is managed by SAP AI Core.

</td>
</tr>
</table>



<a name="loiob0b935b86cc944e2875ba01321ff3fc6__section_dy5_x3y_bzb"/>

## Models

**For more information about available models, including conversion rates for tokens, rate limits and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**

For more information about models and their parameters, see the documentation from the model provider.



Models from Azure OpenAI are accessed through a private instance of the `chat-completions API.` The access points are not publicly accessible, and are accessed through SAP AI Core. For more information, see [Azure OpenAI Chat Completions API](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions).

Open Source models are hosted by SAP AI Core and can be accessed via OpenAI compatible API schema.

For more information on the generative AI hub in SAP AI Core, see [SAP AI Core documentation.](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/Generative-AI-Hub)

-   **[Models and Scenarios in the Generative AI Hub](models-and-scenarios-in-the-generative-ai-hub-fef463b.md)**  

-   **[Tutorial](tutorial-c0018f1.md " ")**  

-   **[Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-96b65bb.md "You make a model available for use by creating a deployment. You can do so one time for each model and model version, and for each
		resource group that you want to use with generative AI hub.")**  
You make a model available for use by creating a deployment. You can do so one time for each model and model version, and for each resource group that you want to use with generative AI hub.
-   **[Model Library](model-library-fce6fea.md "Explore available models and their specifications. Inform your model choice using
		benchmarking data.")**  
Explore available models and their specifications. Inform your model choice using benchmarking data.
-   **[Grounding Management](grounding-management-0ee0f52.md "The grounding management app lets you manage the lifecycle of your data pipelines.")**  
The grounding management app lets you manage the lifecycle of your data pipelines.
-   **[Chat](chat-d84b5a1.md "
		
	")**  

-   **[Orchestration](orchestration-4953dc1.md "The orchestration service runs on SAP AI Core under the global AI scenario
                orchestration. It provides unified access to multiple generative AI models through consistent
            code, configuration, and deployment.")**  
The orchestration service runs on SAP AI Core under the global AI scenario `orchestration`. It provides unified access to multiple generative AI models through consistent code, configuration, and deployment.
-   **[Administration](administration-3d03a2e.md "")**  


**Related Information**  


[Azure Chat Completions Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

[Tiiuae Falcon 40b Instruct Documentation](https://huggingface.co/tiiuae/falcon-40b-instruct)

