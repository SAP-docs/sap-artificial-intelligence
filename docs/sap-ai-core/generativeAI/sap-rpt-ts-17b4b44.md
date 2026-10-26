<!-- loio17b4b4493eb74e7c9f7142f784eae6dd -->

# SAP-RPT-TS

SAP-RPT-TS is a pretrained time series foundation model from SAP that provides high-quality forecasts for business time series data such as demand, sales, and operational metrics without requiring training or fine-tuning.

SAP-RPT-TS extends the RPT model family from static tabular data to temporal and sequential data. The model is designed to deliver highly accurate forecasts with low prediction error rates for enterprise time series use cases.

SAP-RPT-TS uses in-context learning to generate forecasts directly from historical time series data. By providing recent observations and optionally related series or covariates, you can obtain forecasts without training or fine-tuning a model.

The model returns probabilistic forecasts as predictive distributions rather than single point estimates. This enables uncertainty quantification and supports more informed business decisions.

You can generate forecasts directly through a single API call by providing the required historical context.



## Key Features

-   **Pretrained Model:** Use the model immediately without collecting training datasets, managing training infrastructure, or running model training cycles.
-   **Fast and Lightweight:** The compact architecture delivers low-latency forecasts and runs efficiently on standard CPU infrastructure, reducing deployment costs and simplifying scaling across multiple time series.
-   **In-Context Learning:** Provide recent historical observations during inference and receive forecasts instantly without creating or maintaining individual forecasting models.
-   **Flexible Data Structures:** Support univariate and multivariate targets, multiple target variables, past covariates, and known future covariates to improve forecast accuracy.
-   **Probabilistic and Grounded:** Generate calibrated prediction intervals in addition to forecast values, helping reduce the risk of overprediction or underprediction.



## SAP-RPT-TS Models

SAP-RPT-TS is currently available in the following model version:

-   `sap-rpt-ts and version : 1`

**Model Specifications**


<table>
<tr>
<th valign="top">

Specification

</th>
<th valign="top">

sap-rpt-ts-1

</th>
</tr>
<tr>
<td valign="top">

Maximum Context Length

</td>
<td valign="top">

8192 rows

</td>
</tr>
<tr>
<td valign="top">

Maximum Horizon Steps

</td>
<td valign="top">

1024

</td>
</tr>
<tr>
<td valign="top">

Recommended Feature Columns

</td>
<td valign="top">

1–128 columns

</td>
</tr>
</table>

Supported input structures include univariate targets, multivariate targets, past covariates, and future covariates.



## Workflow

You can access SAP-RPT-TS through the `foundation-models` scenario using the executable ID `aicore-sap`.

To use the model, create a configuration and then create a deployment using the following values:

-   **Executable ID:** `aicore-sap`
-   **Model Name:** `sap-rpt-ts and version : 1`
-   **Model Version:** Specify a version or use `latest`.

For more information about deployments, see [Create a Deployment](create-a-deployment-b32e7a8.md).

After deployment, consume the model through API calls. For sample requests and responses, see [Inference Request Overview](inference-request-overview-97e58a1.md).



## Costs

To estimate projected costs, use the SAP AI Core cost calculator and select the SAP-RPT-TS model. For more information, see [SAP AI Core Cost Calculator for Generative AI](https://ai-core-calculator.cfapps.eu10.hana.ondemand.com/uimodule/index.html#/gen).



## Best Practices

To achieve the best forecasting results, follow these recommendations.



### Input Data

-   Provide as many historical observations as possible. Short input histories can reduce forecast quality.

-   A single time series can contain up to 8192 observations. Longer series are automatically truncated to the most recent 8192 observations.

-   Set the forecast horizon according to the required prediction length. Values greater than 1024 are automatically truncated to 1024.

-   Use regularly spaced timestamps whenever possible. The model performs best when observations are evenly spaced.

-   A limited number of missing timestamps is supported. Internally generated timestamps must not exceed 20% of the supplied timestamps.

-   Provide past and future covariates whenever available. Forecast quality improves significantly when relevant explanatory variables are supplied.

-   For optimal inference performance, keep the combined number of targets and covariates below 128 per series.




### **Choose an Appropriate Point Forecast Method**

Choose the `point_forecast` method that best matches your loss function and data characteristics:

-   `point_forecast: "median"` returns q=0.5 directly \(MAE-optimal and robust to heavy-tailed distributions\). This is the default option and is recommended for general-purpose forecasting of smooth, continuous demand.

-   `point_forecast: "mean"` approximates the predictive mean by using trapezoidal integration over the `quantile_levels` grid \(MSE/RMSE-optimal\). It is recommended for intermittent demand with many zero values. Use a dense `quantile_levels` grid to improve mean estimation accuracy.

-   `point_forecast: "hierarchical_forecast"` is recommended when the series follows a known aggregation hierarchy, such as country → city → street, and forecasts at all levels must remain consistent. Define the hierarchy using `hierarchical_labels` and specify aggregation levels in `hierarchical_levels`, ordered from the coarsest to the finest level. Use `null` to represent the grand total. The service forecasts each level and reconciles the results using MinT-WLS so that parent forecasts equal the sum of their child forecasts at each horizon step.




### **Control Forecast Output**

-   Set `output_quantile: true` when you need the full predictive distribution \(shape `[n_series][n_variates][K][horizon]`, where K=21\) for custom prediction intervals, client-side point estimators, or pinball-loss evaluation. The `output_quantile` option always returns the fixed 21-quantile grid regardless of `quantile_levels`. The `quantile_levels` option controls only the `selected_quantile_result` field.

-   Use `quantile_levels` when you require only specific quantiles. For example, `[0.1, 0.5, 0.9]` returns only those quantiles in `selected_quantile_result` instead of the full 21-quantile output. For `mean`, the specified quantiles also define the integration grid used to calculate the point forecast.

-   Use `clip_min` and `clip_max` to constrain the point forecast. These settings are applied only to `result` and do not affect `confidence_interval_output` or quantile outputs. As a result, a clipped forecast can fall outside the reported confidence interval.

-   Enable `cross_learning: true` when the time series in a request are related and can benefit from shared information. Leave this option set to `false` \(default\) when the series are unrelated and should be forecast independently.

-   Enable `enhanced_forecast: true` when forecast accuracy is the highest priority. This option applies additional inference techniques that can improve forecast quality at the cost of increased inference time. Input time-point consumption is billed at a flat 4× rate when enabled, regardless of history length or forecast horizon. Forecast horizon points are not multiplied.


> ### Note:  
> The accuracy and fairness of the model's forecasts depend on the quality, length, regularity, and balance of the data provided. Any bias present in the input data can result in biased or skewed outputs. SAP is not responsible for any bias, inaccuracy, or unintended outcome arising from user-provided data.

-   **[Inference Request Overview](inference-request-overview-97e58a1.md)**  

-   **[Sample Inference Requests and Responses](sample-inference-requests-and-responses-c32103c.md "The following examples demonstrate common forecasting scenarios and show how different
		request parameters affect the response returned by the inference service.")**  
The following examples demonstrate common forecasting scenarios and show how different request parameters affect the response returned by the inference service.

