<!-- loio46af3f92dd34440e84f911c1e534898d -->

# Troubleshooting

Use the following troubleshooting information to identify and resolve common validation, service, and performance issues when calling the API.



## Common Validation Errors

-   Error: "Cannot provide both 'rows' and 'columns'"

    Resolution: Provide query data in either `columns` format or `rows` format, but not both.

-   Error: "All columns must have the same number of rows"

    Resolution: Ensure that all column arrays contain the same number of values.

-   Error: "Context columns schema does not match query columns schema"

    Resolution: Ensure that `contextColumns` uses the same column names as `columns`.

-   Error: "Must provide either 'rows' or 'columns' for query data"

    Resolution: Include either `rows` or `columns` in the request.

-   Error: "When using 'rows' for query data, use 'contextRows' for context data"

    Resolution: Use `contextRows` when the request uses `rows` for query data.




## Common Service Errors

-   Error: "SCENARIO\_CONFIG\_NOT\_FOUND\_ERROR"

    Resolution: Verify that the scenario configuration exists in the Context Registry and check the scenario configuration name for typographical errors.

-   Error: "CONTEXT\_SELECTOR\_ERROR"

    Resolution: Verify that the Context Selector service is available, the referenced Tabular Artifact is accessible, and all filter conditions are valid.

-   Error: "MODEL\_NOT\_FOUND"

    Resolution: Verify that `modelName` specifies a supported model and check the model name for typographical errors.

-   Error: "SAP\_RPT1\_SMALL\_ERROR" or "SAP\_RPT1\_LARGE\_ERROR"

    Resolution: Verify that the input data format is valid, the target column exists in the dataset, and the request does not exceed model limits.




## Performance Issues

-   Issue: Requests take longer than 10 seconds.

    Resolution: Reduce the `numRows` value, decrease the number of columns in the query data, use a smaller Tabular Artifact, or use a different context selection strategy.

-   Issue: Requests return a high number of errors.

    Resolution: Verify authentication headers, ensure that the Context Selector and TFM services are available, and check network connectivity to downstream services.




## Performance Optimization

To optimize performance, consider the following recommendations:

-   Use `strategy="none"` if you manage context data outside the orchestration workflow.
-   Use `strategy="random"` for consistent and fast context selection.
-   Use `strategy="heuristic"` when prediction quality is more important than context selection time.
-   Use only the context data required for the prediction task. Larger context datasets can increase context selection and inference time.



## Error Handling

To improve reliability, follow these recommendations:

-   Implement exponential backoff when retrying requests that return 5xx errors.
-   Do not retry requests that return 4xx errors. These errors typically indicate an issue with the request.
-   Use the `X-Correlation-ID` header to troubleshoot failed requests.
-   Validate data schemas before sending requests.
-   Ensure that all columns contain the same number of values in columnar format.
-   Ensure that all row objects contain the same set of keys in row format.
-   Verify that all target columns exist in the query data.
-   Configure client-side timeouts based on your workload requirements. A timeout of 60 to 120 seconds is recommended.
-   Expect longer processing times when using the heuristic strategy with large datasets.
-   Consider asynchronous processing patterns for long-running prediction requests.



## Security Considerations

Consider the following security and data handling recommendations:

-   The service does not persist query data or prediction results.
-   Context data is retrieved for each request from registered Tabular Artifacts.
-   Review data residency requirements when selecting deployment regions.

