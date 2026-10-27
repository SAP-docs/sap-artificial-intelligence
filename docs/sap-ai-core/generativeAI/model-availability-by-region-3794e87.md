<!-- loio3794e87242944b15990fcabf38b82290 -->

# Model Availability by Region

Use this regional availability matrix for AI models to identify which models and versions are available in your specific geographic region.



## How to Read These Tables

In the tables below, models are listed as follows:


<dl>
<dt><b>

Yes

</b></dt>
<dd>

The model is available and accessed from within that region.



</dd><dt><b>

Yes\*

</b></dt>
<dd>

The model is available but may be accessed from a cross-regional location. This setup harmonizes the model offering across data centers and allows for load balancing and failovers, which help to mitigate data center outages. Data centers are selected based on model availability and data center proximity.



</dd><dt><b>

No

</b></dt>
<dd>

The model isn't available in the specified region.



</dd>
</dl>

> ### Example:  
> The model mistralai--mistral-small in region US10 is marked with **Yes\***, meaning that it is likely to be accessed within that region. However, data centers outside US10 may also be used for the purposes outlined. The same model in region EU10 is marked with **Yes**, meaning that it is used only with data centers in EU10.

For more information about models—including information about **pricing**, **retirement**, and **rate limits**—see SAP Note [3437766](https://me.sap.com/notes/3437766). We recommend that you mark this SAP Note as a favorite so that you receive updates whenever it changes.



### Access Types

Models on the generative AI hub can be accessed via remote providers such as AWS Bedrock, or hosted by SAP.

-   **SAP-hosted:** Models are hosted on SAP’s own infrastructure and managed by SAP AI Core.
-   **SAP-managed:** Models are hosted on SAP’s tenant-isolated Hyperscaler infrastructure and managed by SAP AI Core.
-   **Remote:** Models \(such as those provided by AWS\) are hosted and managed by providers, and are accessed via SAP AI Core.



### Model Versions

You have the following options when working with a model:

-   You choose to always have the “latest” version of the model. The latest model version can be found in the table. When a version is deprecated, you are automatically moved to the latest version of the model. Be aware that model behavior can change from version to version.
-   You choose to work with a specific version of a model. In this case, you must check when the version will be deprecated and take appropriate steps.

For more information, see [Create a Deployment](create-a-deployment-b32e7a8.md).



## Asia — Pacific — Japan \(APJ\)

The information provided in these tables is maintained on a best-effort basis. For the authoritative list of models available in your landscape, check the model discovery endpoint `$AI_API_URL/v2/lm/scenarios/foundation-models/models`. For more information, see [Supported Models](supported-models-509e588.md).

> ### Note:  
> Choose the *Columns* dropdown to show or hide additional information about the models.

****


<table>
<tr>
<th valign="top">

Executable ID \(Access Type\)

</th>
<th valign="top">

Model

</th>
<th valign="top">

Version

</th>
<th valign="top">

AP10

Australia \(Sydney\)

</th>
<th valign="top">

AP11

Singapore

</th>
<th valign="top">

AP12

Singapore

</th>
<th valign="top">

AP20

Australia \(Sydney\)

</th>
<th valign="top">

AP21

Australia, Southeast \(Melbourne\)

</th>
<th valign="top">

AP30

Australia \(Sydney\)

</th>
<th valign="top">

IN30

India \(Mumbai\)

</th>
<th valign="top">

JP10

Japan \(Tokyo\)

</th>
<th valign="top">

JP31

Japan \(Tokyo/Osaka\)

</th>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-lite

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-lite

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-micro

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-premier

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-pro

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-image

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-text

</td>
<td valign="top">

1.2

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-text

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-haiku

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-opus

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-sonnet

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.6-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.6-sonnet

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.7-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.8-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-hosted\)

</td>
<td valign="top">

cohere--command-a-reasoning

</td>
<td valign="top">

2508 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-managed\)

</td>
<td valign="top">

cohere-reranker

</td>
<td valign="top">

3.5 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-managed\)

</td>
<td valign="top">

cohere-rerank-pro

</td>
<td valign="top">

4

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash

</td>
<td valign="top">

001 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash-image

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-pro

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.1-flash-image

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.1-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.5-flash

</td>
<td valign="top">

001 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.5-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.8-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3-pro-image

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-embedding

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-embedding-2

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1-mini

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1-nano

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-05-13

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-08-06 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-11-20

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o-mini

</td>
<td valign="top">

2024-07-18

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.1

</td>
<td valign="top">

2025-11-13 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.2

</td>
<td valign="top">

2025-12-11

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.3-codex

</td>
<td valign="top">

2026-02-24

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.4

</td>
<td valign="top">

2026-03-05

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.4-nano

</td>
<td valign="top">

2026-03-17

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.5

</td>
<td valign="top">

2026-04-24

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-luna

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-sol

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-terra

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5-mini

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5-nano

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-realtime

</td>
<td valign="top">

2025-08-28

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-large-instruct

</td>
<td valign="top">

2407 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-medium

</td>
<td valign="top">

3.5

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-medium-instruct

</td>
<td valign="top">

2505 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-small

</td>
<td valign="top">

2603

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-small-instruct

</td>
<td valign="top">

2503 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-nvidia \(SAP-managed\)

</td>
<td valign="top">

nvidia--llama-3.2-nv-embedqa-1b

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o1

</td>
<td valign="top">

2024-12-17

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o3

</td>
<td valign="top">

2025-04-16

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o3-mini

</td>
<td valign="top">

2025-01-31

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o4-mini

</td>
<td valign="top">

2025-04-16

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-abap-1

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.5

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.5-large

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.6

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.6-large

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1-large

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1-small

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

perplexity-ai \(remote\)

</td>
<td valign="top">

sonar

</td>
<td valign="top">

perplexity-us

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

perplexity-ai \(remote\)

</td>
<td valign="top">

sonar-pro

</td>
<td valign="top">

perplexity-us

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

prior-labs \(SAP-hosted\)

</td>
<td valign="top">

tabpfn-3.5-plus

</td>
<td valign="top">

2609

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-3-large

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-3-small

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-ada-002

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6-astra

</td>
<td valign="top">

2026-09-03

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6-luna

</td>
<td valign="top">

2026-09-22

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6.1-sol

</td>
<td valign="top">

2026-09-22

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-ts

</td>
<td valign="top">

version

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

meta--llama-guard-3-8b

</td>
<td valign="top">

202407

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

ibm--granite-guardian-8b

</td>
<td valign="top">

4.1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
</table>



## Europe — Middle East — Africa \(EMEA\)

The information provided in these tables is maintained on a best-effort basis. For the authoritative list of models available in your landscape, check the model discovery endpoint `$AI_API_URL/v2/lm/scenarios/foundation-models/models`. For more information, see [Supported Models](supported-models-509e588.md).

> ### Note:  
> Choose the *Columns* dropdown to show or hide additional information about the models.

****


<table>
<tr>
<th valign="top">

Executable ID \(Access Type\)

</th>
<th valign="top">

Model

</th>
<th valign="top">

Version

</th>
<th valign="top">

AE01

UAE \(Dubai\)

</th>
<th valign="top">

EU01

Europe \(Rot\)

</th>
<th valign="top">

EU02

Europe \(Frankfurt\)

</th>
<th valign="top">

EU10

Europe \(Frankfurt\)

</th>
<th valign="top">

EU11

Europe \(Frankfurt\)

</th>
<th valign="top">

EU20

Europe \(Netherlands\)

</th>
<th valign="top">

EU30

Europe \(Frankfurt\)

</th>
<th valign="top">

SA30

Saudi Arabia \(Dammam\)

</th>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-lite

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-lite

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-micro

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-premier

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-pro

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-image

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-text

</td>
<td valign="top">

1.2

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-text

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-haiku

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-opus

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-sonnet

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.6-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.6-sonnet

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.7-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.8-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-hosted\)

</td>
<td valign="top">

cohere--command-a-reasoning

</td>
<td valign="top">

2508 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-managed\)

</td>
<td valign="top">

cohere-reranker

</td>
<td valign="top">

3.5 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-managed\)

</td>
<td valign="top">

cohere-rerank-pro

</td>
<td valign="top">

4

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash

</td>
<td valign="top">

001 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash-image

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-pro

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.1-flash-image

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.1-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.5-flash

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.8-flash

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.5-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3-pro-image

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-embedding

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-embedding-2

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1-mini

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1-nano

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-05-13

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-08-06 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-11-20

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o-mini

</td>
<td valign="top">

2024-07-18

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.1

</td>
<td valign="top">

2025-11-13 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.2

</td>
<td valign="top">

2025-12-11

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.3-codex

</td>
<td valign="top">

2026-02-24

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.4

</td>
<td valign="top">

2026-03-05

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.4-nano

</td>
<td valign="top">

2026-03-17

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.5

</td>
<td valign="top">

2026-04-24

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-luna

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-sol

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-terra

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5-mini

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5-nano

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-realtime

</td>
<td valign="top">

2025-08-28

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-large-instruct

</td>
<td valign="top">

2407 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-medium

</td>
<td valign="top">

3.5

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-medium-instruct

</td>
<td valign="top">

2505 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-small

</td>
<td valign="top">

2603

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-small-instruct

</td>
<td valign="top">

2503 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-nvidia \(SAP-managed\)

</td>
<td valign="top">

nvidia--llama-3.2-nv-embedqa-1b

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o1

</td>
<td valign="top">

2024-12-17

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o3

</td>
<td valign="top">

2025-04-16

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o3-mini

</td>
<td valign="top">

2025-01-31

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o4-mini

</td>
<td valign="top">

2025-04-16

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-abap-1

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.5

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.5-large

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.6

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.6-large

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1-large

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1-small

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

perplexity-ai \(remote\)

</td>
<td valign="top">

sonar

</td>
<td valign="top">

perplexity-us

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

perplexity-ai \(remote\)

</td>
<td valign="top">

sonar-pro

</td>
<td valign="top">

perplexity-us

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

prior-labs \(SAP-hosted\)

</td>
<td valign="top">

tabpfn-3.5-plus

</td>
<td valign="top">

2609

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-3-large

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-3-small

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-ada-002

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6-astra

</td>
<td valign="top">

2026-09-03

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6-luna

</td>
<td valign="top">

2026-09-22

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6.1-sol

</td>
<td valign="top">

2026-09-22

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-ts

</td>
<td valign="top">

version

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

meta--llama-guard-3-8b

</td>
<td valign="top">

202407

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

ibm--granite-guardian-8b

</td>
<td valign="top">

4.1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
</table>



## Americas \(AMER\)

The information provided in these tables is maintained on a best-effort basis. For the authoritative list of models available in your landscape, check the model discovery endpoint `$AI_API_URL/v2/lm/scenarios/foundation-models/models`. For more information, see [Supported Models](supported-models-509e588.md).

> ### Note:  
> Choose the *Columns* dropdown to show or hide additional information about the models.

****


<table>
<tr>
<th valign="top">

Executable ID \(Access Type\)

</th>
<th valign="top">

Model

</th>
<th valign="top">

Version

</th>
<th valign="top">

BR10

Brazil \(São Paulo\)

</th>
<th valign="top">

CA10

Canada \(Montréal\)

</th>
<th valign="top">

US10

US East \(N. Virginia\)

</th>
<th valign="top">

US20

US West \(Oregon\)

</th>
<th valign="top">

US21

US East \(Virginia\)

</th>
<th valign="top">

US30

US Central \(Iowa\)

</th>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-lite

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-lite

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-micro

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-premier

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--nova-pro

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-image

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-text

</td>
<td valign="top">

1.2

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

amazon--titan-embed-text

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-haiku

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-opus

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.5-sonnet

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.6-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.6-sonnet

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.7-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aws-bedrock \(AWS\)

</td>
<td valign="top">

anthropic--claude-4.8-opus

</td>
<td valign="top">

1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-hosted\)

</td>
<td valign="top">

cohere--command-a-reasoning

</td>
<td valign="top">

2508 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-managed\)

</td>
<td valign="top">

cohere-reranker

</td>
<td valign="top">

3.5 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-cohere \(SAP-managed\)

</td>
<td valign="top">

cohere-rerank-pro

</td>
<td valign="top">

4

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash

</td>
<td valign="top">

001 \(latest\)

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash-image

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-2.5-pro

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.1-flash-image

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.1-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.5-flash

</td>
<td valign="top">

001 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.8-flash

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3.5-flash-lite

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-3-pro-image

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-embedding

</td>
<td valign="top">

001

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

gcp-vertexai \(Google\)

</td>
<td valign="top">

gemini-embedding-2

</td>
<td valign="top">

001

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1-mini

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4.1-nano

</td>
<td valign="top">

2025-04-14

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-05-13

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-08-06 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o

</td>
<td valign="top">

2024-11-20

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-4o-mini

</td>
<td valign="top">

2024-07-18

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.1

</td>
<td valign="top">

2025-11-13 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.2

</td>
<td valign="top">

2025-12-11

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.3-codex

</td>
<td valign="top">

2026-02-24

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.4

</td>
<td valign="top">

2026-03-05

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.4-nano

</td>
<td valign="top">

2026-03-17

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.5

</td>
<td valign="top">

2026-04-24

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-luna

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-sol

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5.6-terra

</td>
<td valign="top">

2026-07-09

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5-mini

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-5-nano

</td>
<td valign="top">

2025-08-07

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-realtime

</td>
<td valign="top">

2025-08-28

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-large-instruct

</td>
<td valign="top">

2407 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-medium

</td>
<td valign="top">

3.5

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-medium-instruct

</td>
<td valign="top">

2505 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-small

</td>
<td valign="top">

2603

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-mistralai \(SAP-hosted\)

</td>
<td valign="top">

mistralai--mistral-small-instruct

</td>
<td valign="top">

2503 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-nvidia \(SAP-managed\)

</td>
<td valign="top">

nvidia--llama-3.2-nv-embedqa-1b

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o1

</td>
<td valign="top">

2024-12-17

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o3

</td>
<td valign="top">

2025-04-16

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o3-mini

</td>
<td valign="top">

2025-01-31

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

o4-mini

</td>
<td valign="top">

2025-04-16

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-abap-1

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.5

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.5-large

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.6

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1.6-large

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1-large

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-1-small

</td>
<td valign="top">

1

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

perplexity-ai \(remote\)

</td>
<td valign="top">

sonar

</td>
<td valign="top">

perplexity-us

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

perplexity-ai \(remote\)

</td>
<td valign="top">

sonar-pro

</td>
<td valign="top">

perplexity-us

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

prior-labs \(SAP-hosted\)

</td>
<td valign="top">

tabpfn-3.5-plus

</td>
<td valign="top">

2609

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-3-large

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-3-small

</td>
<td valign="top">

1 \(latest\)

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

text-embedding-ada-002

</td>
<td valign="top">

2 \(latest\)

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6-astra

</td>
<td valign="top">

2026-09-03

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6-luna

</td>
<td valign="top">

2026-09-22

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

azure-openai \(Azure\)

</td>
<td valign="top">

gpt-6.1-sol

</td>
<td valign="top">

2026-09-22

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-sap \(SAP-hosted\)

</td>
<td valign="top">

sap-rpt-ts

</td>
<td valign="top">

version

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

meta--llama-guard-3-8b

</td>
<td valign="top">

202407

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
<tr>
<td valign="top">

aicore-opensource

</td>
<td valign="top">

ibm--granite-guardian-8b

</td>
<td valign="top">

4.1

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes\*

</td>
<td valign="top">

Yes\*

</td>
</tr>
</table>



## Compliance

SAP AI Core, including generative AI hub must **not** be used to generate synthetic data for training or fine-tuning models. Any exceptions must be explicitly approved and documented.

You are responsible for making sure that your use of AI models on the generative AI hub complies with applicable laws, regulations, rules, and corporate policies. Note that this statement does not modify SAP's obligations under your agreement for the use of the generative AI hub.

