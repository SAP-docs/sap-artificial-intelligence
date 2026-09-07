<!-- loio76b292cf8ea44e369de3a9fdc2751a1c -->

# SAP-RPT-1.5

SAP-RPT-1.5 is a relational pre-trained transformer for prediction tasks on structured and relational data. It's developed and maintained by SAP.

For general information about the SAP-RPT model family, including key features, tabular in-context learning, deployment instructions, API usage, and response formats, see [SAP-RPT-1](sap-rpt-1-f128f5e.md) overview.



## SAP RPT Models

`SAP-RPT-1.5` is available in the following model versions:

-   `sap-rpt-1.5` supports medium-complexity prediction scenarios. It is optimized for low latency and high prediction throughput.

-   `sap-rpt-1.5-large` supports complex prediction scenarios. It is optimized for high prediction quality and low error rates.


> ### Note:  
> SAP-RPT-1.5 predicts multiple target columns together. As a result, predictions can differ when you predict multiple target columns in a single request instead of predicting each target column separately.

**Model Specifications**


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

sap-rpt-1.5

</th>
<th valign="top">

sap-rpt-1.5-large

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

1024<sup>\*</sup> 

</td>
</tr>
<tr>
<td valign="top">

Recommended Context Length

</td>
<td valign="top">

500-2000 rows<sup>\+</sup> 

</td>
<td valign="top">

4000-8000 rows<sup>\+</sup> 

</td>
</tr>
</table>

Both model versions support up to 512 rows and 10 columns per prediction request. Supported task types are `classification` and `regression`.

\* Number of target classes does not represent a hard limit. SAP recommends these values to achieve optimal prediction quality. Depending on the use case, larger numbers of target classes can also produce high-quality predictions.

\+ Recommended context lengths are based on SAP experimentation and represent best-practice values that balance prediction quality, runtime, and cost. Depending on the application scenario and business requirements, different settings can provide better results. SAP recommends testing with production data to identify the optimal configuration.



## Explainability

`SAP-RPT-1.5` supports explainability capabilities that help you understand how the model generates predictions.

For information about explainability, request parameters, response fields, and example requests and responses, see SAP RPT [SAP RPT 1.5 Explainability](sap-rpt-1-5-explainability-24b28d5.md).

-   **[SAP RPT 1.5 Explainability](sap-rpt-1-5-explainability-24b28d5.md)**  


