<!-- loio77ebfe5b28ef4442aff752cfe26a0db7 -->

# Create an Evaluation



<a name="loio77ebfe5b28ef4442aff752cfe26a0db7__prereq_xy4_mkn_s2c"/>

## Prerequisites

-   You have prepared your dataset and registered it as an artifact. For more information, see [Register Evaluation Artifacts](register-evaluation-artifacts-19412e0.md).

-   You have chosen your metric types. If you're using custom metrics, you've prepared your custom metric. For more information, see [System-Defined Evaluation Metrics](system-defined-evaluation-metrics-2ac6a08.md)and [Custom Metrics](custom-metrics-35dcc3e.md).

-   If your prompt template variable names and test data attribute names are mismatched, you have prepared your variable mapping. For more information, see [Variable Mapping](variable-mapping-56727a3.md).

-   You have registered an object store with the name `default`. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-54068a9.md).

-   For custom metrics only: you've prepared your custom metrics. For more information, see [Custom Metrics](custom-metrics-35dcc3e.md).
-   You have created a prompt for your evaluation, and your prompt is available in the prompt registry for your evaluation. For more information, see [Prompt Registry](prompt-registry-5392e7d.md).



## Create a Configuration

To create a configuration, send a POST request to endpoint `{{apiurl}}/v2/lm/configurations`.

Include the `artifactId` for your registered dataset as `inputArtifactBindings`.

Include the `executableId` `"genai-evaluations-simplified"`

Include the following in your request as `parameterBindings`:


<table>
<tr>
<th valign="top" colspan="2">

Input Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

`datasetFolder` 

</td>
<td valign="top">

An AI Core artifact whose path points to the root folder in the object store containing the test dataset for evaluation.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`testDataset` 

</td>
<td valign="top">

A JSON containing the path to a test dataset relative to the rootFolder and a file type.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`metrics` 

</td>
<td valign="top">

The IDs of metrics to be evaluated. A string containing comma-separated names of system-defined metrics, or IDs of custom metrics.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`variableMapping` \(Optional\)

</td>
<td valign="top">

A JSON containing column name mappings. For more information, see [Variable Mapping](variable-mapping-56727a3.md).

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`tags`\(Optional\)

</td>
<td valign="top">

A JSON containing name-value pairs containing user-defined metadata

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`orchestrationDeploymentURL` 

</td>
<td valign="top">

The orchestration deployment to use for orchestration completion and LLM-as-a-judge completion calls.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`repetitions`\(Optional\)

</td>
<td valign="top">

The number of times the same input is submitted to the LLM to evaluate the consistency of the LLM outputs. Should be greater than 1 if specified. Default is 1.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`testRowCount`\(Optional\)

</td>
<td valign="top">

Specifies the number of rows to be selected from the testDataset for evaluation.

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

A reference to your prompt template and models or to your orchestration config

</td>
<td valign="top">

`promptTemplate` and `models` combined.

</td>
<td valign="top">

-   The ID of the prompt template stored in the prompt registry.
-   The models that correspond to the prompt template.

    A string containing a comma-separated list of models and their versions. For example, `"gpt-4.1:latest, gpt-4o-mini:latest"`.|




</td>
</tr>
<tr>
<td valign="top">

`orchestrationRegistryIds`

</td>
<td valign="top">

The ID of the orchestration config stored in the orchestration registry.

</td>
</tr>
</table>



### Example with `promptTemplate` and `models` combined

> ### Sample Code:  
> ```
> curl --request POST "$AI_API_URL/v2/lm/configurations" \
> --header "Authorization: Bearer $TOKEN" \
> --header "AI-Resource-Group: $RESOURCE_GROUP" \
> --header "Content-Type: application/json" \
> --data '{
>     "name": "genai-eval-conf",
>     "scenarioId": "genai-evaluations",
>     "executableId": "genai-evaluations-simplified",
>     "inputArtifactBindings": [
>         {
>             "key": "datasetFolder",
>             "artifactId": "<artifactId>"
>         }
>     ],
>     "parameterBindings": [
>         {
>             "key": "repetitions",
>             "value": "1"
>         },
>         {
>             "key": "orchestrationDeploymentURL",
>             "value": "https://<ai-api-base-url.com>/v2/inference/deployments/<deploymentId>"
>         },
>         {
>             "key": "tags",
>             "value": "{}"
>         },
>         {
>             "key": "variableMapping",
>             "value": "{"json_schema_match/json_schema":"data/json_schema_value"}"
>         },
>         {
>             "key": "metrics",
>             "value": "BERT Score,BLEU,ROUGE,"
>         },
>         {
>             "key": "testDataset",
>             "value": "{"path":"data/template_variables.csv", "type": "csv"}"
>         },
>         {
>             "key": "promptTemplate",
>             "value": "<promptTemplateId>"
>         },
>         {
>             "key": "models",
>             "value": "<model>:latest, <model>:latest"
>         },
>     ]
> }'
> ```



### Example with `orchestrationRegistryIds`

> ### Sample Code:  
> ```
> curl --request POST "$AI_API_URL/v2/lm/configurations" \
> --header "Authorization: Bearer $TOKEN" \
> --header "AI-Resource-Group: $RESOURCE_GROUP" \
> --header "Content-Type: application/json" \
> --data '{
>     "name": "genai-eval-conf",
>     "scenarioId": "genai-evaluations",
>     "executableId": "genai-evaluations-simplified",
>     "inputArtifactBindings": [
>         {
>             "key": "datasetFolder",
>             "artifactId": "<artifactId>"
>         }
>     ],
>     "parameterBindings": [
>         {
>             "key": "repetitions",
>             "value": "1"
>         },
>         {
>             "key": "orchestrationDeploymentURL",
>             "value": "https://<ai-api-base-url.com>/v2/inference/deployments/<deploymentId>"
>         },
>         {
>             "key": "tags",
>             "value": "{}"
>         },
>         {
>             "key": "variableMapping",
>             "value": "{"json_schema_match/json_schema":"data/json_schema_value"}"
>         },
>         {
>             "key": "metrics",
>             "value": "BERT Score,BLEU,ROUGE,"
>         },
>         {
>             "key": "testDataset",
>             "value": "{"path":"data/template_variables.csv", "type": "csv"}"
>         },
>           { "key": "orchestrationRegistryIds", 
>             "value": "<orchestrationConfigId>" },
>     ]
> }'
> ```

You will receive a configuration ID. Note the ID for the next step.



## Start an Evaluation

To start an evaluation, send a POST request to endpoint `$AI_API_URL/v2/lm/executions`: Include your configuration ID in your request.

For example:

> ### Sample Code:  
> ```
> curl --request POST "$AI_API_URL/v2/lm/executions" 
> --header "Authorization: Bearer $TOKEN" 
> --header "AI-Resource-Group: $RESOURCE_GROUP" 
> --header "Content-Type: application/json" \
> --data '{
> "configurationId": "<configurationID>"
> }'
> ```



## Results

Your evaluation will take some time to run. To check the status of an evaluation, send a GET request to endpoint `{{apiurl}}/v2/lm/executions/{{executionid}}`.



## Next Steps

The evaluation outputs the following:

-   An SQLite DB file which stores the orchestration input, orchestration output, values for all the metrics calculated for this orchestration output and statistics such as latency for this orchestration output. These metric values are called raw metric values. This SQLite DB file is stored in the object store as an AI Core output artifact.
-   A set of metrics whose values are aggregated from the raw metric values. The aggregate metrics are stored in the tracking service. The user-defined tags along with the run names are stored with the metrics. Post evaluation completion the runs generated by the workload along with the aggregate metrics can be seen by calling the tracking api.

When the evaluation is complete, you can view and analyze your results. For more information, see [View Evaluation Results](view-evaluation-results-aa46126.md).

After and evaluation is complete, there may be residual output artifacts such as logs or instance level metrics, that can be safely deleted by users.

