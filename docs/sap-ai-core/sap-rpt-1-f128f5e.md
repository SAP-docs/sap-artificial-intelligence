<!-- loiof128f5e12e40452f997a278fcff88bf5 -->

# SAP-RPT-1

`SAP-RPT-1` is a relational pretrained transformer for use on relational and structured data. It's developed and maintained by SAP.

Relational Foundation Models \(RFMs\) are large-scale machine learning models designed to understand, represent, and reason about relationships between entities in structured or semi-structured data.

RFMs are useful for tasks such as knowledge graph completion, recommendation systems, complex query answering, and any application where understanding the connections and interactions between different entities is crucial.

`SAP-RPT-1` is a table-native model aiming to achieve highest prediction quality and lowest error rates for predictions on tabular business data. It's pretrained, and doesn't need additional training or fine-tuning steps.

You can get predictions directly in one API call from provided context examples.



## Key Features

Key features include:

-   **Pretrained Model:** Removes the need to collect training datasets, manage compute infrastructure, or wait weeks for model training cycles. Deploy immediately with production-ready accuracy.

-   **In-Context Learning:** Accepts representative context examples during inference time to return instant predictions without the need for setup or customization for your specific use cases.

-   **Fast Iterations and Adaptation:** Adapts to the context data provided in your requests, without the need for additional training steps or deployments.

-   **Grounded to Business:** Produces predictions that are grounded in the provided context examples, resulting in a lower risk of prediction errors or hallucinations.




## Tabular In-Context Learning

`SAP-RPT-1` produces predictions through tabular in-context learning.

Prompts are given in table form. They contain context examples and fields marked for prediction with a placeholder value.

> ### Example:  
> The following prompt shows a table where cost centers are associated with ordered products. A placeholder value \(`[PREDICT]`\) has been used to request a prediction for the `COSTCENTER` of the couch. `SAP-RPT-1` returns proposals for the prediction request. Multiple requests can be included in one table prompt.
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> PRODUCT
> 
> </th>
> <th valign="top">
> 
> PRICE
> 
> </th>
> <th valign="top">
> 
> ORDERDATE
> 
> </th>
> <th valign="top">
> 
> ID
> 
> </th>
> <th valign="top">
> 
> COSTCENTER
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> Couch
> 
> </td>
> <td valign="top">
> 
> 999.99
> 
> </td>
> <td valign="top">
> 
> 28-11-2025
> 
> </td>
> <td valign="top">
> 
> 35
> 
> </td>
> <td valign="top">
> 
> `[PREDICT]` 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Office Chair
> 
> </td>
> <td valign="top">
> 
> 150.8
> 
> </td>
> <td valign="top">
> 
> 02-11-2025
> 
> </td>
> <td valign="top">
> 
> 44
> 
> </td>
> <td valign="top">
> 
> Office Furniture
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Server Rack
> 
> </td>
> <td valign="top">
> 
> 2200.00
> 
> </td>
> <td valign="top">
> 
> 01-11-2025
> 
> </td>
> <td valign="top">
> 
> 104
> 
> </td>
> <td valign="top">
> 
> Data Infrastructure
> 
> </td>
> </tr>
> </table>



## Model Versions

`SAP-RPT-1` has the following versions:

-   `sap-rpt-1-small`, which is recommended when:

    -   Prediction scenarios are of medium complexity.
    -   Low latency and high-prediction throughput are the primary objective.

-   `sap-rpt-1-large`, which is recommended when:

    -   Prediction scenarios are complex.
    -   Best prediction quality and lowest error rates are the primary objective.


**Model Specifications**


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

`sap-rpt-1-small` 

</th>
<th valign="top">

`sap-rpt-1-large` 

</th>
</tr>
<tr>
<td valign="top">

Max. Context Length

</td>
<td valign="top">

2048 rows

</td>
<td valign="top">

65536 rows

</td>
</tr>
<tr>
<td valign="top">

Max. Columns

</td>
<td valign="top">

100 columns

</td>
<td valign="top">

256 columns

</td>
</tr>
<tr>
<td valign="top">

Number of Target Classes \(Classification\)

</td>
<td valign="top">

256<sup>\*</sup> 

</td>
<td valign="top">

1024\*

</td>
</tr>
<tr>
<td valign="top">

Recommended Context Length

</td>
<td valign="top">

500–2000 rows<sup>\+</sup> 

</td>
<td valign="top">

4000–8000 rows<sup>\+</sup> 

</td>
</tr>
</table>

Both model versions allow up to 128 simultaneous prediction rows and up to 10 simultaneous prediction columns in each prediction request. Supported task types are `classification` and `regression`.

\* The number of target classes is a recommendation for best prediction quality, not a hard limit. Depending on the specific use case, models can produce high-quality predictions for larger numbers of target classes.

\+ Generic recommendations on context length are best practice values based on internal tests, balancing prediction quality, model runtime, and costs. Optimal settings vary across use cases and data sets, so customers or implementation partners must conduct their own testing with production data to achieve the best results for their specific scenario.



## Workflow

You can access coding models through the `foundation-models` scenario and the `aicore-sap` executable ID.

To use a model through the `foundation-models` scenario, you must create a configuration and deployment. You need the `executableId`: `aicore-sap` and `modelVersion`: `sap-rpt-1-small` or `sap-rpt-1-large`. For more information, see [Create a Deployment](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide-dev/activate-generative-ai-hub-for-sap-ai-core#create-a-deploymentl).

You consume the model through API calls. For more information, see [Example Payloads for Inferencing - sap-rpt-1](example-payloads-for-inferencing-sap-rpt-1-399566e.md).

**Parent topic:**[Models](models-6440777.md "")

**Related Information**  


[Large Language Models](large-language-models-c45166a.md "Large Language Models (LLMs) are trained on vast amounts of text data to understand and generate human-like language.LLMs are useful for tasks such as text generation, summarization, translation, question answering, and conversational AI.")

[Supported Models](supported-models-509e588.md "")

