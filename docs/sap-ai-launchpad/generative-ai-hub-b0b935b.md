<!-- loiob0b935b86cc944e2875ba01321ff3fc6 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Generative AI Hub

The Generative AI Hub incorporates generative AI into your AI activities in SAP AI Core and SAP AI Launchpad.



<a name="loiob0b935b86cc944e2875ba01321ff3fc6__section_k14_k3y_bzb"/>

## Scenarios

Access to the large language models is provided under the global AI scenario `foundation-models`, which is managed by SAP AI Core. Individual models are provided as executables in the form of serving templates, and accessed by choosing the corresponding template for the desired model.

The following scenarios are available:


<table>
<tr>
<th valign="top">

Scenario Number

</th>
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

1

</td>
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

2

</td>
<td valign="top">

foundation-models

</td>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

Opensource models hosted and accessed via SAP AI Core.

</td>
</tr>
</table>



<a name="loiob0b935b86cc944e2875ba01321ff3fc6__section_dy5_x3y_bzb"/>

## Models

The following models are supported:


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

Deprecation \(as Specified by Model Provider\)

YYYY-MM-DD

</th>
<th valign="top">

Region

</th>
<th valign="top">

Request Limit \(Requests per Minute\)

</th>
</tr>
<tr>
<td valign="top">

azure-openai

</td>
<td valign="top">

gpt-35-turbo

</td>
<td valign="top">

0613

</td>
<td valign="top">

2024-06-13

</td>
<td valign="top">

-   US10 \(mapped to Azure US East\)
-   EU10 \(mapped to Azure EU Central\)



</td>
<td valign="top">

120

</td>
</tr>
<tr>
<td valign="top">

azure-openai

</td>
<td valign="top">

gpt-35-turbo-16k

</td>
<td valign="top">

0613

</td>
<td valign="top">

2024-06-13

</td>
<td valign="top">

-   US10 \(mapped to Azure US East\)
-   EU10 \(mapped to Azure EU Central\)



</td>
<td valign="top">

96

</td>
</tr>
<tr>
<td valign="top">

azure-openai

</td>
<td valign="top">

gpt-4

</td>
<td valign="top">

0613

</td>
<td valign="top">

2024-07-05

</td>
<td valign="top">

-   US10 \(mapped to Azure US East\)
-   EU10 \(mapped to Azure EU Central\)



</td>
<td valign="top">

18

</td>
</tr>
<tr>
<td valign="top">

azure-openai

</td>
<td valign="top">

gpt-4-32k

</td>
<td valign="top">

0613

</td>
<td valign="top">

2024-07-05

</td>
<td valign="top">

-   US10 \(mapped to Azure US East\)
-   EU10 \(mapped to Azure EU Central\)



</td>
<td valign="top">

78

</td>
</tr>
<tr>
<td valign="top">

azure-openai

</td>
<td valign="top">

text-embedding-ada-002

</td>
<td valign="top">

2

</td>
<td valign="top">

2025-04-04

</td>
<td valign="top">

-   US10 \(mapped to Azure US East\)
-   EU10 \(mapped to Azure EU Central\)



</td>
<td valign="top">

138

</td>
</tr>
<tr>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

tiiuae--falcon-40b-instruct

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

-   US10 \(mapped to Azure US East\)
-   EU10 \(mapped to Azure EU Central\)



</td>
<td valign="top">

138

</td>
</tr>
</table>

> ### Note:  
> Rate limits are applied at tenant level.



Models from Azure OpenAI are accessed through a private instance of the `chat-completions API`. For more information, see [Azure OpenAI Chat Completions API Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions).

Open Source models are hosted by SAP AI Core and can be accessed via OpenAI compatible API schema.

For more information on the Generative AI Hub in SAP AI Core, see [SAP AI Core documentation.](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/Generative-AI-Hub)

-   **[Models and Scenarios in the Generative AI Hub](models-and-scenarios-in-the-generative-ai-hub-729dd9e.md)**  

-   **[Tutorial](tutorial-c0018f1.md "The activation and consumption steps are also available online in a step by step tutorial. ")**  
The activation and consumption steps are also available online in a step by step tutorial.
-   **[Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-96b65bb.md "You make a model available for use by creating a deployment. You can do so one time for each model and model version, and for each
		resource group that you want to use with Generative AI Hub.")**  
You make a model available for use by creating a deployment. You can do so one time for each model and model version, and for each resource group that you want to use with Generative AI Hub.

**Related Information**  


[Azure Chat Completions Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions)

[Tiiuae Falcon 40b Instruct Documentation](https://huggingface.co/tiiuae/falcon-40b-instruct)

