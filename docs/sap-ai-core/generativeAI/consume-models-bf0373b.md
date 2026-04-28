<!-- loiobf0373b1cf2a4680a7044e1a562d3853 -->

# Consume Models

The generative AI hub helps you to complete tasks like summarizing text, inferencing, and transforming content. To do so, you consume a generative AI model by sending a request to the model's endpoint.



<a name="loiobf0373b1cf2a4680a7044e1a562d3853__prereq_nzn_mdw_tyb"/>

## Prerequisites

You have the deployment URL for your generative AI model. For more information, see [Create a Deployment](create-a-deployment-b32e7a8.md).



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
> Don't store personal data in prompts when using the generative AI hub. Personal data is any data that can be used alone, or in combination, to identify the person that the data refers to.



## Procedure

Consume your generative AI deployment using your deployment URL and the example payloads provided. For more information, see the following:

-   [Mistral](mistral-6ab293a.md)
-   [NVIDIA](nvidia-69a6249.md)
-   [Cohere](cohere-17d02ac.md)
-   [Perplexity](perplexity-736025c.md)
-   [OpenAI](openai-490f55d.md)
-   [Vertex AI](vertex-ai-8bb3519.md)
-   [AWS Bedrock](aws-bedrock-6a81f85.md)
-   [SAP-RPT-1](sap-rpt-1-f128f5e.md)
-   [SAP-ABAP-1](sap-abap-1-d197270.md)

-   **[Supported Parameters](supported-parameters-55d2197.md "The chat completions API supports a range of parameters that influence model responses, influencing aspects like creativity, length, and
		formatting of the output. ")**  
The chat completions API supports a range of parameters that influence model responses, influencing aspects like creativity, length, and formatting of the output.

