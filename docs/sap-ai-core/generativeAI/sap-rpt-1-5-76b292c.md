<!-- loio76b292cf8ea44e369de3a9fdc2751a1c -->

# SAP-RPT-1.5

SAP-RPT-1.5 is a relational pretrained transformer for prediction tasks on structured and relational data. It's developed and maintained by SAP.

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

`SAP-RPT-1.5` supports an explainability feature that provides insight into how the model generates predictions.

You can enable explainability by adding an `explanations` configuration to `prediction_config` in the request.

> ### Note:  
> Column scores and relevant context rows are derived from model internals and do not indicate causality. Results can be less accurate for small datasets. For strongly correlated features, the model can distribute scores across multiple feature columns instead of assigning a high score to a single column.

**Request Parameters**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`prediction_config.explanations` 

</td>
<td valign="top">

object

</td>
<td valign="top">

Optional configuration used to request explanations. The default value is `null`.

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.explanations.top_column_scores` 

</td>
<td valign="top">

integer

</td>
<td valign="top">

Optional. Number of top column scores to return. The default value is `0`. A value of `0` disables explainability. The maximum value is `20`.

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.explanations.top_relevant_context_rows` 

</td>
<td valign="top">

integer

</td>
<td valign="top">

Optional. Number of most relevant context rows to return for each query row. The maximum value is `20`.

</td>
</tr>
</table>

**Example Request**

Add the `explanations` object to `prediction_config`. See [SAP-RPT-1](sap-rpt-1-f128f5e.md) overview.

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
    "explanations": {
        "top_column_scores": 3,
        "top_relevant_context_rows": 2
    }
}

```

**Response Fields**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`explanations` 

</td>
<td valign="top">

object or null

</td>
<td valign="top">

Explanation data containing column scores and relevant context rows. Present only when explainability is enabled.

</td>
</tr>
<tr>
<td valign="top">

`explanations.top_column_scores` 

</td>
<td valign="top">

array or null

</td>
<td valign="top">

Array of objects, one for each query row, mapping feature column names to attention-based importance scores.

</td>
</tr>
<tr>
<td valign="top">

`explanations.top_relevant_context_rows` 

</td>
<td valign="top">

array or null

</td>
<td valign="top">

Contains the indices of the most relevant context rows for each query row, sorted by relevance. Indices are zero-based.

</td>
</tr>
</table>

**Example Response with Explanations**

```

{
  "id": "c334f854-0d70-4c79-bd73-9ac581fd8cda",
  "status": {
    "code": 0,
    "message": "ok"
  },
  "predictions": [
    {
      "COSTCENTER": [
        {
          "prediction": "Office Furniture",
          "confidence": 0.96,
          "confidence_interval": null
        }
      ],
      "ID": "35"
    }
  ],
  "explanations": {
    "top_column_scores": [
      {
        "PRODUCT": 0.523,
        "PRICE": 0.234,
        "ORDERDATE": 0.121
      }
    ],
    "top_relevant_context_rows": [
      [1, 2]
    ]
  },
  "metadata": {
    "num_columns": 5,
    "num_rows": 2,
    "num_predictions": 1,
    "num_query_rows": 1
  }
}

```

