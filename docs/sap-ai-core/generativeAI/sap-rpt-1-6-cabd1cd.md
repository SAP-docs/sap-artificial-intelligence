<!-- loiocabd1cd5bb1e4426a915b7646ca38259 -->

# SAP-RPT-1.6

SAP-RPT-1.6 is a relational pre-trained transformer for prediction tasks on structured and relational data. It supports classification and regression tasks and is developed and maintained by SAP.

For general information about the SAP-RPT model family, including key features, tabular in-context learning, deployment instructions, API usage, and response formats, see [SAP-RPT-1](sap-rpt-1-f128f5e.md) overview.



## SAP-RPT Models

`SAP-RPT-1.6` is available in the following model versions:

-   `sap-rpt-1.6` supports medium-complexity prediction scenarios. It is optimized for low latency and high prediction throughput.

-   `sap-rpt-1.6-large` supports complex prediction scenarios. It is optimized for high prediction quality and low error rates.


> ### Note:  
> SAP-RPT-1.6 predicts multiple target columns together. As a result, predictions can differ when you predict multiple target columns in a single request instead of predicting each target column separately.

**Model Specifications**


<table>
<tr>
<th valign="top">

**Value**

</th>
<th valign="top">

**sap-rpt-1.6**

</th>
<th valign="top">

**sap-rpt-1.6-large**

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

Max. Query Length

</td>
<td valign="top">

512 rows

</td>
<td valign="top">

512 rows

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

Max. Target Columns

</td>
<td valign="top">

10

</td>
<td valign="top">

10

</td>
</tr>
<tr>
<td valign="top">

Number of Target Classes \(Classification\)

</td>
<td valign="top">

250<sup>1</sup>

</td>
<td valign="top">

5000<sup>1</sup>

</td>
</tr>
<tr>
<td valign="top">

Recommended Context Length

</td>
<td valign="top">

500-2000 rows<sup>2</sup>

</td>
<td valign="top">

4000-36000 rows<sup>2</sup>

</td>
</tr>
</table>

Supported task types are `classification` and `regression`.

<sup>1</sup> Number of target classes does not represent a hard limit. SAP recommends these values to achieve optimal prediction quality. Depending on the use case, larger numbers of target classes can also produce high-quality predictions.

<sup>2</sup> Recommended context lengths are based on SAP experimentation and represent best-practice values that balance prediction quality, runtime, and cost. Depending on the application scenario and business requirements, different settings can provide better results. SAP recommends testing with production data to identify the optimal configuration.



## Context Mode

`sap-rpt-1.6-large` supports the optional `context_mode` parameter in the `prediction_config` object.

The `context_mode` parameter enables higher prediction accuracy when a large number of context rows is available.

> ### Note:  
> Setting `context_mode` to `deep` increases prediction latency. SAP recommends using deep context mode only when more than 8000 context rows are available and additional prediction accuracy is required.

SAP recommends evaluating `sap-rpt-1.6` first. If additional accuracy is required, use `sap-rpt-1.6-large` with the default context mode before enabling deep context mode.

**Request Parameters**


<table>
<tr>
<th valign="top">

**Name**

</th>
<th valign="top">

**Type**

</th>
<th valign="top">

**Description**

</th>
</tr>
<tr>
<td valign="top">

`prediction_config.context_mode` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Optional. The default value is `default`. Use `default` for the best balance between accuracy and latency. Use `deep` only with `sap-rpt-1.6-large` when more than 8000 context rows are available and higher accuracy is required.

</td>
</tr>
</table>

**Example Request**

```

"prediction_config": {
    "target_columns": [
        {
            "name": "COSTCENTER",
            "prediction_placeholder": "[PREDICT]",
            "task_type": "classification",
            "top_k": 1
        }
    ],
    "context_mode": "deep"
}

```



## Explainability

`SAP-RPT-1.6` supports explainability capabilities that help you understand how the model generates predictions.

For information about explainability, request parameters, response fields, and example requests and responses, see SAP RPT [SAP RPT 1.6 Explainability](sap-rpt-1-6-explainability-92a0ffe.md).

-   **[SAP RPT 1.6 Explainability](sap-rpt-1-6-explainability-92a0ffe.md)**  


