<!-- loio509e588cd26949a59da96aca3397e7b8 -->

# Supported Models

You can find information about available models, including token conversion rates, rate limits, and deprecation dates, in SAP Note [3437766](https://me.sap.com/notes/3437766).


<table>
<tr>
<td valign="top">

![](images/Document_Report_32b935e.png)

-   [SAP Note 3437766](https://me.sap.com/notes/3437766)



</td>
<td valign="top">

Go to SAP Note [3437766](https://me.sap.com/notes/3437766).

</td>
</tr>
</table>

You can retrieve a list of available models and model versions using the model discovery endpoint. Send a GET request to endpoint `$AI_API_URL/v2/lm/scenarios/foundation-models/models`. The base URL is the URL of your SAP AI Core environment. This can also be set as an environment variable.

Include the following headers in your request:

-   Authorization: Bearer <your-access-token\>
-   content-type: application/json
-   AI-Resource-Group: <your-resource-group\>

For example:

```
curl --location '$AI_API_URL/v2/lm/scenarios/foundation-models/models' \
--header 'AI-Resource-Group: <your-resource-group>' \
--header 'Authorization: Bearer $AUTH_TOKEN'

```

Example response

> ### Output Code:  
> ```
> {
>   "count": integer,
>   "resources": [
>     {
>       "accessType": "Remote",
>       "allowedScenarios": [
>         {
>           "executableId": "<executable Id>",
>           "scenarioId": "foundation-models"
>         },
>         {
>           "executableId": "orchestration",
>           "scenarioId": "orchestration"
>         }
>       ],
>       "description": "<model description>",
>       "displayName": "<model display name>",
>       "executableId": "<executable ID>",
>       "model": "<model ID>",
>       "provider": "<Provider>",
>       "versions": [
>         {
>           "capabilities": [
>             "text-generation"
>           ],
>           "contextLength": integer,
>           "cost": [
>             {
>               "inputCost": integer
>             },
>             {
>               "outputCost": integer
>             }
>           ],
>           "deprecated": Boolean,
>           "inputTypes": [
>             "text"
>           ],
>           "isLatest": Boolean,
>           "metadata": [
>             {
>               "meanWinRate": integer
>             },
>             {
>               "chatBotArenaScore": integer
>             },
>             {
>               "helmCapabilitiesAccuracyMeanScore": integer
>             }
>           ],
>           "name": "<name>",
>           "retirementDate": "",
>           "streamingSupported": Boolean
>         }
>       ]
>     },
>     # ...
>   ]
> }
> ```

The output can include the following parameters:


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

Number of models available

</td>
</tr>
<tr>
<td valign="top">

accessType

</td>
<td valign="top">

Type of access for the model \(for example, "Remote"\)

</td>
</tr>
<tr>
<td valign="top">

allowedScenarios

</td>
<td valign="top">

List of scenarios and executables where the model can be used

</td>
</tr>
<tr>
<td valign="top">

description

</td>
<td valign="top">

Description of the model

</td>
</tr>
<tr>
<td valign="top">

displayName

</td>
<td valign="top">

Display name of the model

</td>
</tr>
<tr>
<td valign="top">

executableId

</td>
<td valign="top">

Executable under which the model is available, required at the time of creating Deployment configuration

</td>
</tr>
<tr>
<td valign="top">

model

</td>
<td valign="top">

Required as modelName at the time of creating Deployment configuration

</td>
</tr>
<tr>
<td valign="top">

provider

</td>
<td valign="top">

Provider of the model

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

versions\[\].capabilities

</td>
<td valign="top">

List of capabilities of the model version

</td>
</tr>
<tr>
<td valign="top">

versions\[\].contextLength

</td>
<td valign="top">

Maximum context length supported by the model version

</td>
</tr>
<tr>
<td valign="top">

versions\[\].cost

</td>
<td valign="top">

List of cost information \(for example, inputCost, outputCost\)

</td>
</tr>
<tr>
<td valign="top">

versions\[\].deprecated

</td>
<td valign="top">

Boolean indicating if the model version is deprecated

</td>
</tr>
<tr>
<td valign="top">

versions\[\].inputTypes

</td>
<td valign="top">

List of supported input types

</td>
</tr>
<tr>
<td valign="top">

versions\[\].isLatest

</td>
<td valign="top">

Suggests if the modelVersion is latest

</td>
</tr>
<tr>
<td valign="top">

versions\[\].metadata

</td>
<td valign="top">

Additional metadata about the model version

</td>
</tr>
<tr>
<td valign="top">

versions\[\].name

</td>
<td valign="top">

Version name, optional value to provide as modelVersion at the time of creating Deployment Configuration

</td>
</tr>
<tr>
<td valign="top">

versions\[\].retirementDate

</td>
<td valign="top">

Date when the model version will be retired \(if applicable\)

</td>
</tr>
<tr>
<td valign="top">

versions\[\].streamingSupported

</td>
<td valign="top">

Boolean indicating if streaming is supported

</td>
</tr>
</table>

For information about specific models and their parameters, see the documentation from the model providers.

Models from Azure OpenAI are accessed through a private instance of the chat-completions API. These access points aren't publicly available and are accessed through SAP AI Core. For more information, see [Chat completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions) in the Microsoft documentation.

Open Source models are hosted by SAP AI Core and are accessible through an OpenAI-compatible API schema.

