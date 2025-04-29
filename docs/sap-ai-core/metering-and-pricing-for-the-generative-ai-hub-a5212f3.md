<!-- loioa5212f311a0c434382553e8b6a64f56f -->

# Metering and Pricing for the Generative AI Hub

The use of models in the generative AI hub is metered using GenAI tokensand capacity units.

> ### Note:  
> The generative AI hub is available only as part of the Extended service plan.

GenAI tokens correspond to blocks of 1,000 tokens from each model. The number of GenAI tokens you need changes based on the model used and whether the token is for input or output. There are conversion rates that help you figure out how many GenAI tokens you get from the model provider's tokens. The conversion rates apply to blocks of 1,000 input and output model tokens. By referring to these rates, you can work out how many GenAI tokens you're consuming in total. For more information about the supported models and the conversion rates between model tokens and GenAI tokens, see SAP Note [3437766](https://me.sap.com/notes/3437766).

Each record measured in GenAI tokens is converted into billable metric units, known as “capacity units”. For the conversion rate between GenAI tokens and capacity units \(capacity unit values\), see the [SAP BTP Service Description Guide](https://www.sap.com/about/agreements/policies/cloud-platform.html).

> ### Example:  
> This example uses fictitious values.
> 
> For a given request, x input model tokens and y output model tokens are consumed. The corresponding metrics are:
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Model
> 
> </th>
> <th valign="top">
> 
> GenAI Input Tokens
> 
> \(for 1,000 Model Tokens\)
> 
> </th>
> <th valign="top">
> 
> GenAI Output Tokens
> 
> \(for 1,000 Model Tokens\)
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> Sample model
> 
> </td>
> <td valign="top">
> 
> 0.002
> 
> </td>
> <td valign="top">
> 
> 0.003
> 
> </td>
> </tr>
> </table>
> 
> -   Total GenAI tokens = x/1000 \* 0.002 + y/1000 \* 0.003
> -   Capacity units = Total GenAI tokens \* 2.24038 \(capacity unit value\)



<a name="loioa5212f311a0c434382553e8b6a64f56f__section_jyq_v21_1fc"/>

## Cost Projection

Charges associated with the use of other SAP AI Core components may also apply. For more information, see [SAP AI Core Metering and Pricing](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/metering-and-pricing).

> ### Recommendation:  
> For an estimate of projected costs, use the SAP AI Core cost calculator. For more information, see [Cost Calculator.](https://ai-core-calculator.cfapps.eu10.hana.ondemand.com/uimodule/index.html) 

To see detailed consumption information in SAP BTP cockpit, navigate through the global account menu to *Usage*, filter by service SAP AI Core, and choose *Export*. The report contains generative AI hub model consumption under *Applications* and resource group level consumption under *instance*.

For more information, see [Monitoring Usage and Consumption Costs in Your Global Account in SAP BTP.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/de6f0db8919f4e6f97e54bc4ddaf2ab8.html)

