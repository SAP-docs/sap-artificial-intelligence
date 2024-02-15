<!-- loioa5212f311a0c434382553e8b6a64f56f -->

# Metering and Pricing for the Generative AI Hub

The use of large language models \(LLMs\) in the generative AI hub is metered using GenAI tokensand capacity units.

The Generative AI Hub is available only as part of the Extended service plan.

A GenAI token corresponds to a block of 1,000 tokens from the LLM service provider. Its cost varies depending on the model used and the type of token \(input or output\).

The following table provides the conversion rates between tokens from the LLM service provider and GenAI tokens. The rates apply to blocks of 1,000 input and output tokens. You can refer to these values to calculate the total number of GenAI tokens that you consume.

> ### Note:  
> Values indicated are subject to change.


<table>
<tr>
<th valign="top">

Model

</th>
<th valign="top">

GenAI Input Tokens

\(for 1,000 Tokens\)

</th>
<th valign="top">

GenAI Output Tokens

\(for 1,000 Tokens\)

</th>
</tr>
<tr>
<td valign="top">

GPT-35-Turbo

</td>
<td valign="top">

0.000210

</td>
<td valign="top">

0.00274

</td>
</tr>
<tr>
<td valign="top">

GPT-35-Turbo-16K

</td>
<td valign="top">

0.00403

</td>
<td valign="top">

0.00532

</td>
</tr>
<tr>
<td valign="top">

GPT-4

</td>
<td valign="top">

0.03886

</td>
<td valign="top">

0.07756

</td>
</tr>
<tr>
<td valign="top">

GPT-4-32K

</td>
<td valign="top">

0.07756

</td>
<td valign="top">

0.15496

</td>
</tr>
<tr>
<td valign="top">

text-embedding-ada-002

</td>
<td valign="top">

0.00029

</td>
<td valign="top">

0.00000

</td>
</tr>
<tr>
<td valign="top">

tiiuae--falcon-40b-instruct

</td>
<td valign="top">

0.00101

</td>
<td valign="top">

0.00181

</td>
</tr>
</table>

> ### Example:  
> This example uses fictitious values. For the current conversion rates, see the [SAP BTP Service Description Guide](https://www.sap.com/about/agreements/policies/cloud-platform.html).
> 
> For a given request, x input tokens are consumed and y output tokens are consumed. The corresponding metrics are:
> 
> -   Capacity units = x/1000 \* 0.000210 + y/1000 \* 0.00274

Charges associated with use of SAP AI Core may also apply. For more information, see [SAP AI Core Metering and Pricing](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/metering-and-pricing).

