<!-- loiob0b935b86cc944e2875ba01321ff3fc6 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Generative AI Hub

The generative AI hub incorporates generative AI into your AI activities in SAP AI Core and SAP AI Launchpad.



<a name="loiob0b935b86cc944e2875ba01321ff3fc6__section_k14_k3y_bzb"/>

## Scenarios

Access to generative AI models is provided under the global AI scenario `foundation-models`, which is managed by SAP AI Core. Individual models are provided as executables in the form of serving templates, and accessed by choosing the corresponding template for the desired model.

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

Open source models hosted and accessed through SAP AI Core.

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

AWS Bedrock provides access to Foundation models from Anthropic, Amazon and other providers.

</td>
</tr>
</table>



<a name="loiob0b935b86cc944e2875ba01321ff3fc6__section_dy5_x3y_bzb"/>

## Models

You can use the following models with the generative AI hub:

> ### Note:  
> Models indicated and their associated values are subject to change.

For more information about these models, including conversion rates for tokens, rate limits and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).

For more information about models and their parameters, see the documentation from the model provider.

****


<table>
<tr>
<th valign="top">

Executable ID

</th>
<th valign="top">

Model Name

</th>
<th valign="top">

Model Version

</th>
<th valign="top">

More Information

</th>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`gpt-35-turbo`

</td>
<td valign="top">

0613

1106

</td>
<td valign="top">

[Azure Chat Completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

</td>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`gpt-35-turbo-16k`

</td>
<td valign="top">

0613

</td>
<td valign="top">

[Azure Chat Completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

</td>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`gpt-4`

</td>
<td valign="top">

0613

</td>
<td valign="top">

[Azure Chat Completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

</td>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`gpt-4-32k`

</td>
<td valign="top">

0613

</td>
<td valign="top">

[Azure Chat Completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

</td>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`text-embedding-ada-002`

</td>
<td valign="top">

2

</td>
<td valign="top">

[Embeddings](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#embeddings)

</td>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`text-embedding-3-small`

</td>
<td valign="top">

N/A

</td>
<td valign="top">

[Embeddings](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#embeddings)

</td>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`text-embedding-3-large`

</td>
<td valign="top">

N/A

</td>
<td valign="top">

[Embeddings](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#embeddings)

</td>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`gpt-4o`

</td>
<td valign="top">

2024-05-13

</td>
<td valign="top">

[Azure Chat Completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

</td>
</tr>
<tr>
<td valign="top">

`azure-openai`

</td>
<td valign="top">

`gpt-4`

</td>
<td valign="top">

turbo-2024-04-09

</td>
<td valign="top">

[Azure Chat Completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

</td>
</tr>
<tr>
<td valign="top">

`aicore-opensource`

</td>
<td valign="top">

`tiiuae--falcon-40b-instruct`

</td>
<td valign="top">

N/A

</td>
<td valign="top">

[Tiiuae Falcon 40b Instruct](https://huggingface.co/tiiuae/falcon-40b-instruct)

</td>
</tr>
<tr>
<td valign="top">

`aicore-opensource`

</td>
<td valign="top">

`mistralai--mixtral-8x7b-instruct-v01`

</td>
<td valign="top">

N/A

</td>
<td valign="top">

[Mistral AI](https://huggingface.co/mistralai/Mixtral-8x7B-Instruct-v0.1)

</td>
</tr>
<tr>
<td valign="top">

`aicore-opensource`

</td>
<td valign="top">

`meta--llama3-70b-instruct`

</td>
<td valign="top">

N/A

</td>
<td valign="top">

[Meta](https://huggingface.co/meta-llama/Meta-Llama-3-70B-Instruct)

</td>
</tr>
<tr>
<td valign="top">

`gcp-vertexai`

</td>
<td valign="top">

`text-bison`

</td>
<td valign="top">

002

</td>
<td valign="top">

[GCP Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/text)

</td>
</tr>
<tr>
<td valign="top">

`gcp-vertexai`

</td>
<td valign="top">

`chat-bison`

</td>
<td valign="top">

002

</td>
<td valign="top">

[GCP Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/text-chat)

</td>
</tr>
<tr>
<td valign="top">

`gcp-vertexai`

</td>
<td valign="top">

`textembedding-gecko`

</td>
<td valign="top">

003

</td>
<td valign="top">

[GCP Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/text-embeddings)

</td>
</tr>
<tr>
<td valign="top">

`gcp-vertexai`

</td>
<td valign="top">

`textembedding-gecko-multilingual`

</td>
<td valign="top">

001

</td>
<td valign="top">

[GCP Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/text-embeddings)

</td>
</tr>
<tr>
<td valign="top">

`gcp-vertexai`

</td>
<td valign="top">

`gemini-1.0-pro`

</td>
<td valign="top">

001

</td>
<td valign="top">

[GCP Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/gemini)

</td>
</tr>
<tr>
<td valign="top">

`aws-bedrock`

</td>
<td valign="top">

`anthropic--claude-3-sonnet`

</td>
<td valign="top">

v1

</td>
<td valign="top">

[AWS Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-anthropic-claude-messages.html)

</td>
</tr>
<tr>
<td valign="top">

`aws-bedrock`

</td>
<td valign="top">

`anthropic--claude-3-haiku`

</td>
<td valign="top">

v1

</td>
<td valign="top">

[AWS Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-anthropic-claude-messages.html)

</td>
</tr>
<tr>
<td valign="top">

`aws-bedrock`

</td>
<td valign="top">

`anthropic--claude-3-opus`

</td>
<td valign="top">

v1

</td>
<td valign="top">

[AWS Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-anthropic-claude-messages.html)

</td>
</tr>
<tr>
<td valign="top">

`aws-bedrock`

</td>
<td valign="top">

`amazon--titan-embed-text`

</td>
<td valign="top">

1.2

</td>
<td valign="top">

[AWS Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/titan-embedding-models.html)

</td>
</tr>
<tr>
<td valign="top">

`aws-bedrock`

</td>
<td valign="top">

`amazon--titan-text-lite`

</td>
<td valign="top">

1

</td>
<td valign="top">

[AWS Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/titan-text-models.html)

</td>
</tr>
<tr>
<td valign="top">

`aws-bedrock`

</td>
<td valign="top">

`amazon--titan-text-express`

</td>
<td valign="top">

1

</td>
<td valign="top">

[AWS Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/titan-text-models.html)

</td>
</tr>
</table>



Models from Azure OpenAI are accessed through a private instance of the `chat-completions API.` The access points are not publicly accessible, and are accessed through SAP AI Core. For more information, see [Azure OpenAI Chat Completions API](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions).

Open Source models are hosted by SAP AI Core and can be accessed via OpenAI compatible API schema.

For more information on the generative AI hub in SAP AI Core, see [SAP AI Core documentation.](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/Generative-AI-Hub)

-   **[Models and Scenarios in the Generative AI Hub](models-and-scenarios-in-the-generative-ai-hub-fef463b.md)**  

-   **[Tutorial](tutorial-c0018f1.md " ")**  

-   **[Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-96b65bb.md "You make a model available for use by creating a deployment. You can do so one time for each model and model version, and for each
		resource group that you want to use with generative AI hub.")**  
You make a model available for use by creating a deployment. You can do so one time for each model and model version, and for each resource group that you want to use with generative AI hub.
-   **[Chat](chat-d84b5a1.md "
		
	")**  

-   **[Administration](administration-3d03a2e.md "")**  


**Related Information**  


[Azure Chat Completions Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

[Tiiuae Falcon 40b Instruct Documentation](https://huggingface.co/tiiuae/falcon-40b-instruct)

