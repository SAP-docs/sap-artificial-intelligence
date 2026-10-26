<!-- loio97e58a1ce4234f9bb494b3999e9dae7f -->

# Inference Request Overview

The Time Series Foundation Model provides a single inference endpoint at `$DEPLOYMENT_URL/predict`. The endpoint generates multi-step probabilistic forecasts for one or more time series and supports optional covariates, quantile forecasts, confidence intervals, cross-series learning, hierarchical forecasting, and forecast post-processing.

> ### Tip:  
> If you use a Windows device, use Windows PowerShell and replace `curl` with `curl.exe`.



## Prerequisites

Ensure that you have created and deployed a time series model. For more information, see [Create a Deployment](https://help.sap.com/docs/sap-ai-core/generative-ai/create-deployment-for-generative-ai-model).

Ensure that you've set the following headers:


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

The resource group used in the activation steps.

</td>
</tr>
</table>

Make sure you have set the following variable:

-   **$AI\_API\_URL**: The base URL of your SAP AI Core environment. You can set this URL as an environment variable.


Use the deployment URL as the value of `$DEPLOYMENT_URL` or replace the `$DEPLOYMENT_URL` placeholder in the example requests with your deployment URL.



## Request Payload

All JSON payloads must be UTF-8 encoded.

The `/predict` endpoint accepts a JSON body with three top-level fields: `horizon`, `data` \(a list of series\), and an optional `options` block.



### Forecast Request

```

curl --request POST \
  --url "$DEPLOYMENT_URL/predict" \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{
    "horizon": 3,
    "data": [
        {
            "timestamp": ["<timestamp 1>", "<timestamp 2>", "..."],
            "target": [
                ["<variate 1 timepoint 1>", "<variate 1 timepoint 2>", "..."]
            ],
            "past_covariates": {
                "<covariate name>": ["<value 1>", "<value 2>", "..."]
            },
            "future_covariates": {
                "<covariate name>": ["<value 1>", "<value 2>", "..."]
            }
        }
    ],
    "options": {
        "rules": [
            {
                "covariate": "<future covariate name>",
                "operator": "==",
                "threshold": 1,
                "forecast_value": 0.0
            }
        ],
        "output_quantile": false,
        "point_forecast": "median",
        "quantile_levels": [0.1, 0.5, 0.9],
        "clip_min": 0,
        "clip_max": 100,
        "confidence_interval": 0.80,
        "cross_learning": false,
        "enhanced_forecast": false,
        "hierarchical_labels": [{"<key>": "<value>"}],
        "hierarchical_levels": [null, "<key>"]
    }
}'
      
```



## Parameters



### Top-Level and Per-Series Parameters


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

`horizon`

</td>
<td valign="top">

integer

</td>
<td valign="top">

Required. Must be greater than 0. The number of future steps to forecast.

</td>
</tr>
<tr>
<td valign="top">

`data`

</td>
<td valign="top">

array

</td>
<td valign="top">

Required. A non-empty array of series objects. Each series is forecast independently unless `cross_learning` or `hierarchical_forecast` is used.

</td>
</tr>
<tr>
<td valign="top">

`data[].target`

</td>
<td valign="top">

array

</td>
<td valign="top">

Required. Per-series forecast target values. A list of lists for multivariate series, or a list of numbers for a single-variate series.

`null` values are treated as `NaN`.

Series longer than 8192 points are truncated to the most recent 8192.

</td>
</tr>
<tr>
<td valign="top">

`data[].timestamp`

</td>
<td valign="top">

array

</td>
<td valign="top">

Optional.

A list the same length as `target[i]`, containing at least 2 points.

Supported formats:

-   `int`

-   `YYYY-MM-DD`

-   `YYYY-MM-DD HH:MM:SS`

-   `YYYY-MM-DD HH:MM:SS.<fraction>` \(LONGDATE, fraction up to 7 digits\)

-   `HH:MM:SS` \(time-of-day, midnight rollover supported\)


Regularly-spaced timestamps are expected.

A limited number of missing timestamps are supported. The service uses the smallest gap as the `detected_interval` and fills the unobserved positions before forecasting.

Filled timestamps must not exceed 20% of the supplied timestamps, rounded up.

`result_timestamp` is produced at the detected interval starting after the last observed timestamp.

If omitted, `result_timestamp` and `detected_interval` are `null` for the series.

</td>
</tr>
<tr>
<td valign="top">

`data[].past_covariates`

</td>
<td valign="top">

object

</td>
<td valign="top">

Optional.

An object mapping a covariate name to a list of values.

Each list must match the length of `target[i]`.

Values can be numeric, string, or mixed.

</td>
</tr>
<tr>
<td valign="top">

`data[].future_covariates`

</td>
<td valign="top">

object

</td>
<td valign="top">

Optional.

An object mapping a covariate name to a list of values.

Each list must have a length equal to `horizon`.

Each key must also exist in `past_covariates` of the same series.

</td>
</tr>
</table>



### `options` Parameters

The entire `options` block can be omitted. All fields use default values.


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Type

</th>
<th valign="top">

Default

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`rules`

</td>
<td valign="top">

array

</td>
<td valign="top">

`null`

</td>
<td valign="top">

Deterministic post-processing rules.

For each position in the referenced future covariate array, if the value satisfies `<covariate> <operator> <threshold>`, the forecast at that position is overwritten by `forecast_value`.

Supported operators are `==`, `!=`, `>=`, `<=`, `>`, and `<`.

If multiple rules match the same position, the last matching rule is applied.

Rules take precedence over clipping.

</td>
</tr>
<tr>
<td valign="top">

`output_quantile`

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

`false`

</td>
<td valign="top">

If set to `true`, returns all 21 quantiles in `quantile_result`.

Otherwise, `quantile_result` is `null`.

This value is always `null` for `hierarchical_forecast`.

</td>
</tr>
<tr>
<td valign="top">

`point_forecast`

</td>
<td valign="top">

string

</td>
<td valign="top">

`"median"`

</td>
<td valign="top">

Determines how `result` is calculated.

-   `"median"`: Uses Q0.5 of the quantile output. This option is MAE-optimal and is the default.

-   `"mean"`: Calculates the distribution mean using trapezoidal integration over the predicted quantiles. This option is MSE/RMSE-optimal and is recommended for intermittent demand.

-   `"hierarchical_forecast"`: Performs MinT-WLS reconciliation across aggregation levels. Requires `hierarchical_labels` and `hierarchical_levels`. Reconciled forecasts are returned in `hierarchical_result`, and `result` is returned as `[]`.




</td>
</tr>
<tr>
<td valign="top">

`quantile_levels`

</td>
<td valign="top">

array

</td>
<td valign="top">

`null`

</td>
<td valign="top">

Array of float values in the range \(0,1\).

When specified, the selected levels are returned in `selected_quantile_result`.

If `null`, the default 21-quantile grid is used.

For `mean`, these levels also define the integration grid used to calculate the mean. Using more levels can improve accuracy.

</td>
</tr>
<tr>
<td valign="top">

`clip_min`

</td>
<td valign="top">

number

</td>
<td valign="top">

`null`

</td>
<td valign="top">

Clamps values in `result` that are below the specified value.

</td>
</tr>
<tr>
<td valign="top">

`clip_max`

</td>
<td valign="top">

number

</td>
<td valign="top">

`null`

</td>
<td valign="top">

Clamps values in `result` that are above the specified value.

If both `clip_min` and `clip_max` are specified, `clip_min` must not be greater than `clip_max`.

</td>
</tr>
<tr>
<td valign="top">

`confidence_interval`

</td>
<td valign="top">

number

</td>
<td valign="top">

`0.80`

</td>
<td valign="top">

A value in the range \(0,1\) or `null`.

If specified, `confidence_interval_output` returns the lower and upper quantile bounds for the interval.

For example, a value of `0.80` returns q=0.10 and q=0.90 bounds.

If set to `null`, `confidence_interval_output` is omitted.

This value is always `null` for `hierarchical_forecast`.

</td>
</tr>
<tr>
<td valign="top">

`cross_learning`

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

`false`

</td>
<td valign="top">

If set to `true`, all series in the request are treated as a single group and the model shares information across them.

Results depend on the combination of series included in the request.

No alignment, overlap, or equal-length requirements apply.

If set to `false`, each series is forecast independently.

</td>
</tr>
<tr>
<td valign="top">

`enhanced_forecast`

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

`false`

</td>
<td valign="top">

Applies additional inference techniques to improve forecast accuracy at the cost of increased inference time.

Input time points are billed at a flat 4× rate when enabled.

Output time points are never multiplied.

For more information, see Best Practices.

</td>
</tr>
<tr>
<td valign="top">

`hierarchical_labels`

</td>
<td valign="top">

array

</td>
<td valign="top">

`null`

</td>
<td valign="top">

Array of `{string: string}` dictionaries.

Defines per-series grouping labels for hierarchical reconciliation, with one dictionary for each input series \(leaf\).

Required when `point_forecast` is set to `"hierarchical_forecast"`.

Example:

```
[{"country":"germany","city":"berlin"}, ...]
```



</td>
</tr>
<tr>
<td valign="top">

`hierarchical_levels`

</td>
<td valign="top">

array

</td>
<td valign="top">

`null`

</td>
<td valign="top">

Array of `null` or string values.

Defines the aggregation levels to reconcile, ordered from the coarsest level to the finest level.

Each entry must be either a label key defined in `hierarchical_labels` or `null` to represent the grand total.

The returned `hierarchical_result` tree contains only the levels specified in this parameter. Label keys not specified do not appear as additional hierarchy levels.

Required when `point_forecast` is set to `"hierarchical_forecast"`.

Example:

```
[null, "country"]
```

This example produces a grand-total root node and country-level aggregates.

</td>
</tr>
</table>



## Response Payload

A successful request returns an HTTP 200 response with the following JSON structure. Array fields are shaped by the number of series, variates, and forecast horizon.



### Response Example

```

{
    "result": [
        [
            ["<forecast value 1>", "<forecast value 2>", "..."]
        ]
    ],
    "quantile_result": null,
    "selected_quantile_result": null,
    "confidence_interval_output": [
        [
            [
                ["<lower bound 1>", "<lower bound 2>", "..."],
                ["<upper bound 1>", "<upper bound 2>", "..."]
            ]
        ]
    ],
    "result_timestamp": [
        ["<future timestamp 1>", "<future timestamp 2>", "..."]
    ],
    "detected_interval": [
        {
            "unit": "<interval unit>",
            "value": "<interval value>"
        }
    ],
    "all_null_targets": [],
    "hierarchical_result": null
}
      
```

The response can include the following parameters:


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

`result`

</td>
<td valign="top">

3D array `[n_series][n_variates][horizon]`

</td>
<td valign="top">

Point forecast.

For `median` and `mean`, the values are derived from the 21-quantile output.

For `hierarchical_forecast`, this field always contains `[]`. Use `hierarchical_result` instead.

</td>
</tr>
<tr>
<td valign="top">

`quantile_result`

</td>
<td valign="top">

4D array `[n_series][n_variates][21][horizon]` or `null`

</td>
<td valign="top">

Returns all 21 fixed quantiles when `options.output_quantile` is `true`.

Otherwise, the value is `null`.

The value is always `null` for `hierarchical_forecast`.

Supported quantile levels are:

```
[0.01, 0.05, 0.10, 0.15, 0.20, 0.25, 0.30, 0.35, 0.40, 0.45, 0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 0.99]
```



</td>
</tr>
<tr>
<td valign="top">

`selected_quantile_result`

</td>
<td valign="top">

4D array `[n_series][n_variates][len(quantile_levels)][horizon]` or `null`

</td>
<td valign="top">

Returns quantile forecasts for the requested `quantile_levels`.

If `quantile_levels` is `null`, the value is `null`.

The value is always `null` for `hierarchical_forecast`.

</td>
</tr>
<tr>
<td valign="top">

`confidence_interval_output`

</td>
<td valign="top">

4D array `[n_series][n_variates][2][horizon]` or `null`

</td>
<td valign="top">

Contains lower and upper quantile bounds for the requested `confidence_interval`.

If `confidence_interval` is `null`, the value is `null`.

The value is always `null` for `hierarchical_forecast`.

Index `0` contains the lower bound, and index `1` contains the upper bound.

For example, `confidence_interval=0.80` returns q=0.10 as the lower bound and q=0.90 as the upper bound.

</td>
</tr>
<tr>
<td valign="top">

`result_timestamp`

</td>
<td valign="top">

Array of timestamp arrays or `null` per series

</td>
<td valign="top">

Future timestamps corresponding to forecast steps.

The value is `null` for series that do not include `timestamp` values in the request.

For `hierarchical_forecast`, the value is always `[]`.

</td>
</tr>
<tr>
<td valign="top">

`detected_interval`

</td>
<td valign="top">

Array of `{unit,value}` objects or `null` per series

</td>
<td valign="top">

Represents the interval inferred from the input timestamps.

The value is `null` for series that do not include `timestamp` values in the request.

For `hierarchical_forecast`, the value is always `[]`.

</td>
</tr>
<tr>
<td valign="top">

`hierarchical_result`

</td>
<td valign="top">

Array of tree nodes or `null`

</td>
<td valign="top">

Contains hierarchical aggregate forecasts when `point_forecast` is set to `hierarchical_forecast`.

For all other forecast modes, the value is `null`.

Each node uses the format `{label_value:[[horizon_values]],"__children__":[...]}`.

The forecast values use the shape `[n_variates][horizon]`.

Deepest-level nodes omit the `__children__` field.

If `hierarchical_levels` starts with `null`, the response contains a single root node whose key is an empty string.

Otherwise, the response contains one node for each first-level aggregate, ordered alphabetically.

</td>
</tr>
<tr>
<td valign="top">

`all_null_targets`

</td>
<td valign="top">

Array of `{series_index,target_indices}`

</td>
<td valign="top">

Identifies non-empty target rows that contain only `null` values.

Both indices are zero-based.

The array is empty when no such rows exist.

</td>
</tr>
</table>



## Timestamp Handling

The `detected_interval.unit` value is determined by the input timestamp format.


<table>
<tr>
<th valign="top">

Input Timestamp Format

</th>
<th valign="top">

`detected_interval.unit`

</th>
<th valign="top">

`result_timestamp` Format

</th>
</tr>
<tr>
<td valign="top">

`int`

</td>
<td valign="top">

`integer`

</td>
<td valign="top">

`int`

</td>
</tr>
<tr>
<td valign="top">

`YYYY-MM-DD` \(non-monthly gaps\)

</td>
<td valign="top">

`day`

</td>
<td valign="top">

`YYYY-MM-DD`

</td>
</tr>
<tr>
<td valign="top">

`YYYY-MM-DD` \(calendar-monthly gaps\)

</td>
<td valign="top">

`month`

</td>
<td valign="top">

`YYYY-MM-DD`

</td>
</tr>
<tr>
<td valign="top">

`YYYY-MM-DD HH:MM:SS` \(non-monthly gaps\)

</td>
<td valign="top">

`second`

</td>
<td valign="top">

`YYYY-MM-DD HH:MM:SS`

</td>
</tr>
<tr>
<td valign="top">

`YYYY-MM-DD HH:MM:SS` \(calendar-monthly gaps\)

</td>
<td valign="top">

`month`

</td>
<td valign="top">

`YYYY-MM-DD HH:MM:SS`

</td>
</tr>
<tr>
<td valign="top">

`YYYY-MM-DD HH:MM:SS.<fraction>` \(LONGDATE, non-monthly gaps\)

</td>
<td valign="top">

`1e-7second`

</td>
<td valign="top">

`YYYY-MM-DD HH:MM:SS.<fraction>`

</td>
</tr>
<tr>
<td valign="top">

`YYYY-MM-DD HH:MM:SS.<fraction>` \(LONGDATE, calendar-monthly gaps\)

</td>
<td valign="top">

`month`

</td>
<td valign="top">

`YYYY-MM-DD HH:MM:SS.<fraction>`

</td>
</tr>
<tr>
<td valign="top">

`HH:MM:SS` \(time-of-day\)

</td>
<td valign="top">

`second`

</td>
<td valign="top">

`HH:MM:SS`

</td>
</tr>
</table>

> ### Note:  
> Timestamp strings are interpreted naively. The server does not perform timezone conversion.



## Status Codes and Messages

The service returns standard HTTP status codes.


<table>
<tr>
<th valign="top">

Status

</th>
<th valign="top">

Message

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`200`

</td>
<td valign="top">

OK

</td>
<td valign="top">

Successful forecast.

</td>
</tr>
<tr>
<td valign="top">

`400`

</td>
<td valign="top">

Bad Request

</td>
<td valign="top">

Business validation failed.

The response can be caused by one of the following conditions:

-   Timestamp and target length mismatch.

-   Unsupported timestamp format.

-   Too many missing timestamps to fill \(more than 20% of the supplied timestamps\).

-   A `future_covariates` key that doesn't exist in `past_covariates`.


Response body:

```

{"detail":"<error message>"}
                  
```



</td>
</tr>
<tr>
<td valign="top">

`422`

</td>
<td valign="top">

Unprocessable Content

</td>
<td valign="top">

Schema validation failed.

The response can be caused by one of the following conditions:

-   Missing required field.

-   Wrong data type.

-   Value out of range.

-   Unknown field.


Response body \(FastAPI standard\):

```

{
  "detail": [
    {
      "loc": [...],
      "msg": "...",
      "type": "..."
    }
  ]
}
                  
```



</td>
</tr>
<tr>
<td valign="top">

`500`

</td>
<td valign="top">

Internal Server Error

</td>
<td valign="top">

An unexpected error occurred.

The response can be caused by one of the following conditions:

-   The model crashed.

-   The pipeline wasn't initialized.


Response body:

```

{
  "detail": "Internal server error"
}
                  
```



</td>
</tr>
</table>

