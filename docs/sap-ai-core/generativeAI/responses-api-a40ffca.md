<!-- loioa40ffca12db349898a60c24e64f0789b -->

# Responses API

The Responses API combines the simplicity of the Chat Completions API with the advanced tool-calling capabilities of the legacy Assistants API. It provides a streamlined way to build powerful agentic experiences by enabling developers to structure prompts, invoke tools, and manage outputs within a single API call.



## Prerequisites

-   Ensure that you have a deployment in the RUNNING state for a supported model and access to the DEPLOYMENT\_URL. For more information, see [Create a Deployment](create-a-deployment-b32e7a8.md).

    Ensure that the selected model is listed in SAP Note [3437766](https://me.sap.com/notes/3437766).




## Complete API Reference

For the complete OpenAI Responses API reference, see the Azure Docs on GitHub: [https://github.com/Azure/azure-rest-api-specs/blob/main/specification/ai/data-plane/OpenAI.v1/azure-v1-v1-generated.yaml](https://github.com/Azure/azure-rest-api-specs/blob/main/specification/ai/data-plane/OpenAI.v1/azure-v1-v1-generated.yaml) .

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

Bearer $AUTH\_TOKEN

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
<tr>
<td valign="top">

$DEPLOYMENT\_URL

</td>
<td valign="top">

The deployment URL for your generative AI model. For more information, see [Create a Deployment](create-a-deployment-b32e7a8.md).

Alternatively, you can replace the `$DEPLOYMENT_URL` placeholder in the curl command with your deployment URL.

</td>
</tr>
</table>

-   **[Supported Consumption Methods](supported-consumption-methods-47eb0c7.md "The following features are supported through SAP AI Core. Other
		features cited in the Azure Open AI documentation are not supported.")**  
The following features are supported through SAP AI Core. Other features cited in the Azure Open AI documentation are not supported.
-   **[Lifecycle Management](lifecycle-management-72fb07e.md "Manages the lifecycle of a response created using the OpenAI Responses API. It allows
    you to retrieve a response by ID, cancel an in-progress response, or permanently delete a
    response for cleanup and control purposes.")**  
Manages the lifecycle of a response created using the OpenAI Responses API. It allows you to retrieve a response by ID, cancel an in-progress response, or permanently delete a response for cleanup and control purposes.

