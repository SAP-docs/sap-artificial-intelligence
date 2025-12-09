<!-- loiofef463b24bff4f44a33e98bb1e4f3148 -->

# Models and Scenarios in the Generative AI Hub

The generative AI hub is available in SAP AI Core only with the `extended` service plan.

To use the generative AI hub, you must have one of the following roles or a role collection that contains one of the roles:

-   `genai_manager`

-   `prompt_manager`

-   `genai_experimenter`

-   `prompt_experimenter`


Note that users with only the `genai_experimenter` or `prompt_experimenter` roles cannot save prompts.

For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).



<a name="loiofef463b24bff4f44a33e98bb1e4f3148__section_k14_k3y_bzb"/>

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



<a name="loiofef463b24bff4f44a33e98bb1e4f3148__section_dy5_x3y_bzb"/>

## Models

**For more information about available models, including conversion rates for tokens, rate limits and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**

For more information about models and their parameters, see the documentation from the model provider.



Models from Azure OpenAI are accessed through a private instance of the `chat-completions API.` The access points aren't publicly accessible, and are accessed through SAP AI Core. For more information, see [Azure OpenAI Chat Completions API](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions).

Open Source models are hosted by SAP AI Core and can be accessed via an OpenAI-compatible API schema.



> ### Note:  
> The following topics are out of the scope of this document:
> 
> -   Advanced consumption patterns such as working with a textual knowledge base \(such as embeddings\)
> 
> -   Complex orchestration of LLM calls
> 
> -   Training your own models

