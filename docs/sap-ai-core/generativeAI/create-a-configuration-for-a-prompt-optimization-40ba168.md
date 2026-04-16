<!-- loio40ba1683832d4c3a92eaac8c0c399b18 -->

# Create a Configuration for a Prompt Optimization

Configuration for a prompt optimization defines the parameters, artifacts, and model settings that SAP AI Core uses to execute a prompt optimization.



## Prerequisites

-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.
-   You've registered an object store secret with the name `default` for output artifacts. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-54068a9.md).
-   If you want to separate your input and output object stores, you've registered an object store secret for input artifacts with a name of your choice. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-54068a9.md).
-   You've prepared an optimization dataset and registered it as an optimization artifact. For more information, see [Dataset Preparation](dataset-preparation-b2625d7.md) and [Register Optimization Artifacts](register-optimization-artifacts-b8a9cd8.md).

-   You've prepared a prompt template, and your template is available in the prompt registry. For more information, see [Template Preparation](template-preparation-4526dde.md).

-   If you're using custom metrics, you've prepared your custom metric. For more information, see [Create a Custom Metric](create-a-custom-metric-ab1160e.md).

    > ### Restriction:  
    > Only custom metrics with the evaluation method LLM-as-a-judge and numerical or Boolean output types can be included in prompt optimizations.




## Procedure

Create a configuration by sending a POST request to endpoint `$AI_API_URL/v2/lm/configurations`.

Include the following in your request:


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top" colspan="3">

Value

</th>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top" colspan="3">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
<tr>
<td valign="top">

$RESOURCE\_GROUP

</td>
<td valign="top" colspan="3">

The AI resource group assigned to your account

</td>
</tr>
<tr>
<td valign="top">

$TOKEN

</td>
<td valign="top" colspan="3">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

`inputArtifactBindings` 

</td>
<td valign="top" colspan="3">

The `artifactId` for your registered dataset

</td>
</tr>
<tr>
<td valign="top">

`scenarioId`

</td>
<td valign="top" colspan="3">

`genai-optimizations`

</td>
</tr>
<tr>
<td valign="top">

`executableId`

</td>
<td valign="top" colspan="3">

`genai-optimizations`

</td>
</tr>
<tr>
<td valign="top" rowspan="11">

`parameterBindings` 

</td>
<td valign="top" colspan="2">

`basePrompt` \(mandatory\)

</td>
<td valign="top">

Reference to the prompt in the prompt registry that should be optimized in the format “`<scenario>/<promptName>:<promptVersion>`”

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`baseModel`\(optional\)

</td>
<td valign="top">

In case an evaluation of the selected metric should be run against a baseline model without optimization, to determine the pre-optimization metric. Default: `none`.

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

A dataset selection. Choose from the following:

-   `dataset`: a single dataset that will be split into test and train
-   A combination of `trainDataset` and `testDataset`: a dataset that you have split yourself into test and train, referenced in two parts.

> ### Note:  
> The maximum number of samples across all datasets in an optimization is 200.



</td>
<td valign="top">

`dataset` 

</td>
<td valign="top">

The dataset that is used as basis for optimization. The dataset contains desired responses from the target model. The optimization will maximize the optimization metric by varying the input prompt. This parameter specifies the path to the JSON contained in the input artifact that is submitted as part of the configuration.

The dataset must contain a minimum of 25 samples.

</td>
</tr>
<tr>
<td valign="top">

`trainDataset` \(obligatory if `testDataset` is selected\)

</td>
<td valign="top">

The train dataset used for optimization. The file must be in JSON format and stored in the input artifact. Use this field when you want to provide a dedicated dataset for training instead of using a single dataset.

The dataset must contain a minimum of 25 samples.

</td>
</tr>
<tr>
<td valign="top">

`testDataset` \(obligatory if `trainDataset` is selected\)

</td>
<td valign="top">

The test dataset used to evaluate optimization performance. The file must be in JSON format and stored in the input artifact. Use this field when you provide train and test datasets.

The dataset must contain a minimum of 1 sample.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`promptTemplateScope` \(Optional\)

</td>
<td valign="top">

Defines the scope of the prompt template. Accepted values are `tenant` \(default\) or `resourcegroup`. You can omit this field for tenant‑level templates. You must set it to resource group when the template is created with the `AI-Resource-Group-Scope: true` header.

</td>
</tr>
<tr>
<td valign="top" rowspan="2" colspan="2">

A metric reference \(mandatory\)

The metric to be used for optimizing.

You can choose from:

-   System defined optimization metrics

    To use a system defined optimization metric, include `optimizationMetric`.

-   Your own custom metric. For more information, see [Custom Metrics](custom-metrics-35dcc3e.md).

    To use a custom metric, include `customMetricId`.




</td>
<td valign="top">

The possible system defined optimization metrics are:

-   `LLMaaJ:Sem_Sim_10`

    This metric uses an LLM-as-a-judge to evaluate the semantic similarity of the model response relative to the target golden dataset, on a scale of 1-10.

-   `LLMaaJ:Sem_Sim_1`

    This metric uses an LLM-as-a-judge to evaluate the semantic similarity of the model response relative to the target golden dataset, and returns a binary response.

-   `JSON_Match`

    This metric determines if the LLM's JSON output matches the dataset output. The precision, recall, and f1 scores are computed based on individual fields in the JSON and averaged across all samples in the dataset. This is useful for applications that require structured outputs.




</td>
</tr>
<tr>
<td valign="top">

The ID of your chosen custom metric.

> ### Restriction:  
> Only custom metrics with the evaluation method LLM-as-a-judge **and** numerical **or** Boolean output types can be included in prompt optimizations.



</td>
</tr>
<tr>
<td valign="top" colspan="2">

`targetModels` \(mandatory\)

</td>
<td valign="top">

A comma separated list of models with version for which to optimize the prompt. A prompt can be optimized for a maximum of four models. The format is `<modelName>:<modelVersion>`. The target models must be available in the corresponding region. For more information, see SAP Note [3437766](https://me.sap.com/notes/3437766).

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`targetPromptMapping` \(mandatory\)

</td>
<td valign="top">

Provides a mapping to the optimized prompt for storage in the prompt registry in the format `<modelName>:<modelVersion>=<promptName>:<promptVersion>`.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

prototypeMode \(optional\)

</td>
<td valign="top">

`true` or `false` \(default\).

Prototype mode is not recommended for productive use. For reliable and generalizable results, a larger sample size \(25+ samples\) is needed, and standard mode is recommended.

This mode can be used when you don't have enough data to build a proof-of-concept but want to use a minimum of 3 samples for prototyping.

Number of samples:

-   **Dataset**: Your dataset must contain a minimum of 3 samples.

-   **Split Dataset**: Your train dataset must contain a minimum of 3 samples, and your test dataset must contain a minimum of 1 sample.


Datasets containing more than 200 samples will cause the jobs to fail.

</td>
</tr>
<tr>
<td valign="top">

`includeFewShotExamples` \(optional\)

</td>
<td valign="top" colspan="3">

Whether to include some parts of the provided dataset in the input prompt to improve the output. Default: `false`.

</td>
</tr>
</table>

For example:

> ### Sample Code:  
> ```
> curl --request POST "$AI_API_URL/v2/lm/configurations" \
> --header "Authorization: Bearer $TOKEN" \
> --header "AI-Resource-Group: $RESOURCE_GROUP" \
> --header "Content-Type: application/json" \
> --data '{
>     "name": "genai-eval-conf",
>     "scenarioId": "genai-optimizations ",
>     "executableId": "genai-optimizations ",
>     "inputArtifactBindings": [
>         {
>             "key": "datasetFolder",
>             "artifactId": "1f50fbf8-18d6-4e72-ae10-04fdbc087815"
>         }
>     ],
>     "parameterBindings": [
>         {
>             "key": "basePrompt",
>             "value": "<scenario>/<promptName>:<promptVersion>"
>         },
>         {
>             "key": "dataset",
>             "value": "data.json"
>         {
>             "key": "optimizationMetric",
>             "value": "JSON_Match”
>         },
> 
>         {
>             "key": "promptTemplateScope",
>             "value": "resourcegroup"
>         }, 
>         {
> 
>             "key": "targetModels",
>             "value": "<modelName>:<modelVersion>”
>         },
>         {
>             "key": "targetPromptMapping",
>             "value": “<modelName>:<modelversion>=<promptName>:<promptVersion>”
>         },
>     ]
> }‘
> ```

> ### Note:  
> To use `trainDataset` and `testDataset`, replace the key and value attributes in the `dataset` as shown below.
> 
> ```
> {
>             "key": "trainDataset",
>             "value": "train-dataset.json",
>           }
>           {
>             "key": "testDataset",
>             "value": "test-dataset.json",
>           }
> ```

