<!-- loio0ba2f0ed5a7b4b8d94879fed36f71cac -->

# Choose a Model

Decide which LLM you want to deploy and note the following information:

-   Executable ID

-   Model name

-   Model version

    > ### Note:  
    > -   Instead of specifying a model version, using “latest” will use the latest version of the model available in SAP AI Core.
    > 
    > -   Where the model version is not listed, it is not applicable.
    > 
    > 
    > For more information, see [Model Lifecycle](model-lifecycle-313fe25.md).

    **For more information about available models, including conversion rates for tokens, rate limits and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**


To view the available models, send a GET request to the endpoint: `$AI_API_URL/v2/lm/scenarios/foundation-models/models`.

```
curl --location '$AI_API_URL/v2/lm/scenarios/foundation-models/models' \
--header 'AI-Resource-Group: default' \
--header 'Authorization: Bearer $AUTH_TOKEN'

```

> ### Output Code:  
> ```
> {
>   "count": 41,
>   "resources": [
>     {
>       "accessType": "Remote",
>       "allowedScenarios": [
>         {
>           "executableId": "azure-openai",
>           "scenarioId": "foundation-models"
>         },
>         {
>           "executableId": "orchestration",
>           "scenarioId": "orchestration"
>         }
>       ],
>       "description": "OpenAI GPT-4o engineered for speed and efficiency, supporting text, images and audio using Chat Completions API",
>       "displayName": "GPT-4o",
>       "executableId": "azure-openai",
>       "model": "gpt-4o",
>       "provider": "OpenAI",
>       "versions": [
>         {
>           "capabilities": [
>             "text-generation",
>             "image-recognition"
>           ],
>           "contextLength": 128000,
>           "cost": [
>             {
>               "inputCost": "0.00312"
>             },
>             {
>               "outputCost": "0.0092"
>             }
>           ],
>           "deprecated": false,
>           "inputTypes": [
>             "text",
>             "image",
>             "audio"
>           ],
>           "isLatest": false,
>           "metadata": [
>             {
>               "meanWinRate": "0.938"
>             },
>             {
>               "chatBotArenaScore": "1285"
>             },
>             {
>               "airBenchRefusalRate": "0.528"
>             }
>           ],
>           "name": "2024-05-13",
>           "retirementDate": "",
>           "streamingSupported": true
>         }, ...
> 
>     ]
> }
> ```

The output contains the following parameters, which are needed to create a configuration:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

count

</td>
<td valign="top">

Number of models available description

</td>
</tr>
<tr>
<td valign="top">

description

</td>
<td valign="top">

Description for model

</td>
</tr>
<tr>
<td valign="top">

executableId

</td>
<td valign="top">

Executable under which the model is available, required at the time of creating Deployment configuration model

</td>
</tr>
<tr>
<td valign="top">

model

</td>
<td valign="top">

Required as modelName at the time of creating Deployment configuration versions

</td>
</tr>
<tr>
<td valign="top">

versions

</td>
<td valign="top">

List of available model versions for given model

</td>
</tr>
<tr>
<td valign="top">

versions.name

</td>
<td valign="top">

Optional value to provide as modelVersion at the time of creating Deployment Configuration

</td>
</tr>
<tr>
<td valign="top">

versions.isLatest

</td>
<td valign="top">

Suggests if the modelVersion is latest. See Model Lifecycle for more information

</td>
</tr>
</table>



## Next Steps

You make a model available for use by creating a deployment. For more information, see [Create a Deployment](create-a-deployment-b32e7a8.md).

-   **[Model Lifecycle](model-lifecycle-313fe25.md "")**  


