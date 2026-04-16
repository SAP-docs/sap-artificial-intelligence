<!-- loio4d499ee8abd04dd79ad38b669d3c185c -->

# Model Restriction

When creating a deployment for orchestration, you can restrict the choice of models using an allow or deny list. You can use this to implement internal standards, for example where only certain LLMs are approved for use.

To restrict model access, set the `parametersBindings` to contain `modelFilterList` and `modelFilterListType`.

-   **`modelFilterList`**: a list of `modelNames` and `modelVersions` to be considered.

    If `modelVersions` is not defined, all versions of the given model are considered.

-   **`modelFilterListType`**: a value that controls how `modelFilterList` should be interpreted.

    -   `deny`: excludes the models and defined versions from use within orchestration.

    -   `allow`: only allows the models and defined versions in the modelFilterList to be used within orchestration.



> ### Sample Code:  
> ```
> {
>   "name": "yourNameChoice",
>   "executableId": "orchestration",
>   "scenarioId": "orchestration",
>   "versionId": "0.0.1",
>   "parameterBindings": [
>     {
>       "key": "modelFilterList",
>       "value": "[{\"modelName\": \"gpt-4o-mini\", \"modelVersions\": [\"0613\", \"0301\"]}, {\"modelName\": \"gemini-1.5-pro\", \"modelVersions\": [\"001\"]}]"
>     },
>     {
>       "key": "modelFilterListType",
>       "value": "deny"
>     }
>   ]
> }
> ```

