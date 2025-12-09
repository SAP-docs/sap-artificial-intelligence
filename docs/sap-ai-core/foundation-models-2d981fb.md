<!-- loio2d981fb192f84837a64df26b4983156f -->

# Foundation Models

The foundation models service operates under the global AI scenario `foundation-models`, which is managed by SAP AI Core.

You can access foundation models by creating a deployment for the model that you want to use. To do this, you'll need an auth token from your SAP AI Core instance. For more information, see [Get an Auth Token](get-an-auth-token-0808d42.md) and [Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-b32e7a8.md).

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

aicore-cohere

</td>
<td valign="top">

Cohere models hosted and accessed through SAP AI Core.

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

Models from IBM that are are hosted and managed by SAP and accessed through SAP AI Core.

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

Models from Mistral AI that are hosted and managed by SAP and accessed through SAP AI Core.

</td>
</tr>
<tr>
<td valign="top">

foundation-models

</td>
<td valign="top">

aicore-nvidia 

</td>
<td valign="top">

Models from Nvidia that are hosted and managed by SAP and accessed through SAP AI Core.

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

Open source models that are hosted and managed by SAP and accessed through SAP AI Core.

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

AWS Bedrock provides access to Foundation models from Anthropic, Amazon and other providers.

</td>
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

gcp-vertexai

</td>
<td valign="top">

GCP Vertex AI provides access to PaLM 2 and Gemini models from Google.

</td>
</tr>
</table>

**For more information about available models, including conversion rates for tokens, rate limits and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**

After creating a deployment for your model, you consume the model using prompts. For more information, see [Consume Models](consume-models-bf0373b.md).

-   **[Get an Auth Token](get-an-auth-token-5ec7ec0.md "Start by setting the required environment variables, which you can get from your SAP AI Core instance.")**  
Start by setting the required environment variables, which you can get from your SAP AI Core instance.
-   **[Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-b32e7a8.md "
		
	")**  

-   **[Consume Models](consume-models-bf0373b.md "The generative AI hub helps you
		to complete tasks like summarizing text, inferencing, and transforming content. To do so,
		you consume a generative AI model by sending a request to the model's endpoint.")**  
The generative AI hub helps you to complete tasks like summarizing text, inferencing, and transforming content. To do so, you consume a generative AI model by sending a request to the model's endpoint.
-   **[Foundation Model Tutorials](foundation-model-tutorials-47cedb9.md "We provide tutorials that demonstrate use cases for accessing generative AI models in
		the generative AI hub using foundation
		scenarios. To access each model version, you’ll need to create a separate
		deployment.")**  
We provide tutorials that demonstrate use cases for accessing generative AI models in the generative AI hub using foundation scenarios. To access each model version, you’ll need to create a separate deployment.

