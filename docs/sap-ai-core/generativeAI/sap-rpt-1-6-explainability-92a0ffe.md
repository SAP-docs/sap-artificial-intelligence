<!-- loio92a0ffe903ef4554adb44849e979fad4 -->

# SAP RPT 1.6 Explainability



`SAP-RPT-1.5` and `SAP-RPT-1.6` support an explainability feature that provides insight into how the model generates predictions.

Enable explainability by adding an `explanations` configuration to `prediction_config` in the request.

> ### Note:  
> Column scores and relevant context rows are derived from model internals and do not indicate causality. Results can be less accurate for small datasets. For strongly correlated features, the model can distribute scores across multiple feature columns instead of assigning a high score to a single column.

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

`prediction_config.explanations` 

</td>
<td valign="top">

object

</td>
<td valign="top">

Optional. Configuration used to request explanations. The default value is `null`.

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

**Input Format Guidance**

You can provide input tables as column-wise JSON \(`columns`\), row-wise JSON \(`rows`\), or a Parquet file.

For JSON requests, SAP recommends using `columns` because each column name is sent only once, reducing payload size. Use `rows` when readability is more important than payload size. The service processes requests in the same way regardless of whether you use `columns` or `rows`.

For JSON requests, consider providing the `data_schema` parameter to specify data types. Alternatively, use a Parquet file that contains the appropriate data types.

**Example Request**

Add the `explanations` object to `prediction_config`.

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

Array of objects, one for each query row, that maps feature columns to attention-based importance scores. Higher scores indicate a stronger contribution to the prediction. The service returns only the requested top-k columns.

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

Contains the indices of the most relevant context rows for each query row, sorted by relevance. Indices are zero-based positions in the original input dataset. The service returns only the requested top-k rows.

</td>
</tr>
</table>

**Interpreting top\_relevant\_context\_rows**

The `top_relevant_context_rows` field identifies the rows from the input dataset that contributed most to a prediction. To use these values correctly, keep the same input table that you submitted in the prediction request.

Each value returned in `top_relevant_context_rows` represents a zero-based row position in the original input table. This behavior is the same for row-wise JSON input, column-wise JSON input, and Parquet input.

For JSON requests, column-wise input is typically more compact because each column name is specified only once.

The following example shows a column-wise JSON request:

```
{
  "columns": {
    "id": [1, 2, 3, 4],
    "product": ["Laptop", "Mouse", "Keyboard", "Monitor"],
    "category": ["Electronics", "Accessories", "Accessories", "?"]
  }
}
```

The prediction response can return the following explanation:

```
{
  "explanations": {
    "top_relevant_context_rows": [
      [1, 2]
    ]
  }
}
```

In this example, query row `0` refers to the first prediction row in the response. The values `1` and `2` identify the most relevant rows from the original input table.

The following example retrieves the corresponding rows from the original request payload:

```
input_columns = payload["columns"]

for row_idx in result["explanations"]["top_relevant_context_rows"][0]:
    row = {
        column_name: w_idx]
        for column_name, values in input_columns.items()
    }
    print(f"API row {row_idx}: {row}")
```

The output can look similar to the following:

```
API row 1: {'id': 2, 'product': 'Mouse', 'category': 'Accessories'}
API row 2: {'id': 3, 'product': 'Keyboard', 'category': 'Accessories'}
```

Query row indexes and API input row positions represent different values. Query row index `0` refers to the first item in the response explanation array, while API row positions `1` and `2` refer to rows in the original input table. These values are row positions and not the values from the `id` column.

When using Parquet input, preserve the row order from the uploaded table and use the returned row positions against that same table.

For a complete runnable example that prints row mappings and explanation details, see the sample file `sap-rpt-samples/sap-rpt-1.6/code_samples/python/predict.py` in the SAP RPT samples repository.

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

