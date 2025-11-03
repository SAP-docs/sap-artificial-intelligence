<!-- loio40ba1683832d4c3a92eaac8c0c399b18 -->

# Create a Configuration for an Optimization



## Prerequisites

-   You're using the `extended` service plan. For more information, see [Service Plans](service-plans-c7244c6.md).
-   You've registered an object store secret with the name `default` for output artifacts. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-54068a9.md).
-   If you want to separate your input and output object stores, you've registered an object store secret for input artifacts with a name of your choice. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-54068a9.md).
-   You've prepared an optimization dataset and registered it as an optimization artifact. For more information, see [Dataset preparation](dataset-preparation-b2625d7.md) and [Register Optimization Artifacts](register-optimization-artifacts-b8a9cd8.md).

-   You've prepared a prompt template, and your template is available in the prompt registry. For more information, see [Template preparation](template-preparation-4526dde.md).




## Procedure

Create a configuration by sending a POST request to endpoint `$AI_API_URL/v2/lm/configurations`.

Include the following in your request:


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top" colspan="2">

Value

</th>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top" colspan="2">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
<tr>
<td valign="top">

$RESOURCE\_GROUP

</td>
<td valign="top" colspan="2">

The AI resource group assigned to your account

</td>
</tr>
<tr>
<td valign="top">

$TOKEN

</td>
<td valign="top" colspan="2">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

`inputArtifactBindings`

</td>
<td valign="top" colspan="2">

The `artifactId` for your registered dataset

</td>
</tr>
<tr>
<td valign="top">

`scenarioId`

</td>
<td valign="top" colspan="2">

`genai-optimizations`

</td>
</tr>
<tr>
<td valign="top">

`executableId`

</td>
<td valign="top" colspan="2">

`genai-optimizations`

</td>
</tr>
<tr>
<td valign="top" rowspan="7">

`parameterBindings` 

</td>
<td valign="top">

`basePrompt` \(mandatory\)

</td>
<td valign="top">

Reference to the prompt in the prompt registry that should be optimized in the format “`<scenario>/<promptName>:<promptVersion>`”

</td>
</tr>
<tr>
<td valign="top">

`baseModel`\(optional\)

</td>
<td valign="top">

In case an evaluation of the selected metric should be run against a baseline model without optimization, to determine the pre-optimization metric. Default: `none`.

</td>
</tr>
<tr>
<td valign="top">

`dataset` \(mandatory\)

</td>
<td valign="top">

The dataset that is used as basis for optimization. The dataset contains desired responses from the target model. The optimization will maximize the optimization metric by varying the input prompt. This parameter specifies the path to the json contained in the input artifact that is submitted as part of the configuration. The dataset must contain a minimum of 25 samples and a maximum of 200 samples.

</td>
</tr>
<tr>
<td valign="top">

`optimizationMetric` \(mandatory\)

</td>
<td valign="top">

The metric to be used for optimizing. The possible choices are:

-   `LLMaaJ:Sem_Sim_10`

    This metric uses an LLM-as-a-judge to evaluate the semantic similarity of the model response relative target dataset on a scale of 1-10.


-   `JSON_Match`

    This metric determines if the LLM's JSON output matches the dataset output. The precision, recall, and f1 scores are computed based on individual fields in the JSON and averaged across all samples in the dataset. This is useful for applications that require structured outputs.




</td>
</tr>
<tr>
<td valign="top">

`targetModels` \(mandatory\)

</td>
<td valign="top">

A comma separated list of models with version for which to optimize the prompt. A prompt can be optimized for a maximum of four models. The format is `<modelName>:<modelVersion>`. The target models must be available in the corresponding region. For more information, see SAP Note [3437766](https://me.sap.com/notes/3437766).

</td>
</tr>
<tr>
<td valign="top">

`targetPromptMapping` \(mandatory\)

</td>
<td valign="top">

Provides a mapping to the optimized prompt for storage in the prompt registry in the format `<modelName>:<modelVersion>=<promptName>:<promptVersion>`.

</td>
</tr>
<tr>
<td valign="top">

`includeFewShotExamples` \(optional\)

</td>
<td valign="top">

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
>             "value": "data.json",
>         },
>         {
>             "key": "optimizationMetric",
>             "value": "JSON_Match”
>         },
>         {
> 
>             "key": "targetModels",
>             "value": "<modelName>:<modelVersion>”
>         },
>         {
> 
>             "key": "targetPromptMapping",
>             "value": “<modelName>:<modelversion>=<promptName>:<promptVersion>”
>         },
>     ]
> }‘
> ```

