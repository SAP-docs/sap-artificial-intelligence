<!-- loiobf0373b1cf2a4680a7044e1a562d3853 -->

# Consume Generative AI Models

The generative AI hub helps you to complete tasks like summarizing text, inferencing, and transforming content. To do so, you consume a generative AI model by sending a request to the model's endpoint.



<a name="loiobf0373b1cf2a4680a7044e1a562d3853__prereq_nzn_mdw_tyb"/>

## Prerequisites

You have the deployment URL for your generative AI model. For more information, see [Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-b32e7a8.md).



<a name="loiobf0373b1cf2a4680a7044e1a562d3853__context_wb4_2fc_zyb"/>

## Context

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
</table>

> ### Caution:  
> SAP does not take any responsibility for the quality of the content in the input to or output of the underlying generative AI models. This includes but is not limited to bias, hallucinations, or inaccuracies. The user is responsible for verifying the content.

> ### Caution:  
> Do not store personally identifiable information in prompts when using the generative AI hub. Personally identifiable information is any data that can be used alone, or in combination, to identify the person that the data refers to.



## Procedure

Consume your generative AI deployment using your deployment URL and the example payloads provided. For more information, see the following:

-   [Example Payloads for Inferencing - SAP AI Core Hosted](example-payloads-for-inferencing-sap-ai-core-hosted-951d388.md) for models with `executionId`s indicating a third party provider.
-   [Example Payloads for Inferencing - Remote Models](example-payloads-for-inferencing-remote-models-8c80ea2.md) for models with `executionId`s indicating that a model is hosted on SAP AI Core \(beginning with `aicore-`\).

-   **[Example Payloads for Inferencing - Remote Models](example-payloads-for-inferencing-remote-models-8c80ea2.md)**  

-   **[Example Payloads for Inferencing - SAP AI Core Hosted](example-payloads-for-inferencing-sap-ai-core-hosted-951d388.md)**  

-   **[Supported Parameters](supported-parameters-55d2197.md "The chat completions API supports a range of parameters that influence model responses, influencing aspects like creativity, length, and
		formatting of the output. ")**  
The chat completions API supports a range of parameters that influence model responses, influencing aspects like creativity, length, and formatting of the output.

