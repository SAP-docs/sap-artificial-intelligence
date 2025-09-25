<!-- loioe1c4dd100dfb42ab890e1d95f3516187 -->

# Using the Grounding Module



<a name="loioe1c4dd100dfb42ab890e1d95f3516187__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



## Procedure

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

$RESOURCE\_GROUP

</td>
<td valign="top">

The AI resource group assigned to your account

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
<tr>
<td valign="top">

Bearer $TOKEN

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

config.modules.grounding.type

</td>
<td valign="top">

`"document_grounding_service"`

</td>
</tr>
<tr>
<td valign="top">

config.modules.grounding.config.filters\[\].id

</td>
<td valign="top">

`"filter"`

</td>
</tr>
<tr>
<td valign="top">

config.modules.grounding.config.filters\[\].data\_repositories

</td>
<td valign="top">

Array specifying which repositories to use for document grounding or "\*" to use all available data repositories

</td>
</tr>
<tr>
<td valign="top">

config.modules.grounding.config.filters\[\].search\_config.max\_chunk\_count

</td>
<td valign="top">

Integer that limits the maximum number of chunks to retrieve. Default: `10`

</td>
</tr>
<tr>
<td valign="top">

config.modules.grounding.config.filters\[\].data\_repository\_type

</td>
<td valign="top">

`"vector"`

</td>
</tr>
<tr>
<td valign="top">

config.modules.grounding.config.placeholders.input

</td>
<td valign="top">

A reference to the variable containing your grounding query

</td>
</tr>
<tr>
<td valign="top">

config.modules.grounding.config.placeholders.output

</td>
<td valign="top">

A variable that stores your grounding output

</td>
</tr>
<tr>
<td valign="top">

config.modules.prompt\_templating.prompt.template

</td>
<td valign="top">

Your prompt template

</td>
</tr>
<tr>
<td valign="top">

config.modules.prompt\_templating.model

</td>
<td valign="top">

Your model configuration

</td>
</tr>
<tr>
<td valign="top">

placeholder\_values.groundingRequest

</td>
<td valign="top">

A string containing your grounding query

</td>
</tr>
</table>



<a name="loioe1c4dd100dfb42ab890e1d95f3516187__section_bwz_nhh_jgc"/>

## Examples



### Example with SAP HANA Vector Store, using all “\*” data repositories

> ### Sample Code:  
> ```
> curl --request POST "$ORCH_DEPLOYMENT_URL/v2/completion" \
> --header "content-type: application/json" \
> --header "Authorization: Bearer $TOKEN" \
> --header "AI-Resource-Group: $RESOURCE_GROUP" \
> --data-raw '{
>     "config": {
>         "modules": {
>             "grounding": {
>                 "type": "document_grounding_service",
>                 "config": {
>                     "filters": [
>                         {
>                             "id": "filter",
>                             "data_repositories": [
>                                 "*"
>                             ],
>                             "search_config": {
>                                 "max_chunk_count": 10
>                             },
>                             "data_repository_type": "vector"
>                         }
>                     ],
>                     "placeholders": {
>                         "input": [
>                             "groundingRequest"
>                         ],
>                         "output": "groundingOutput"
>                     }
>                 }
>             },
>             "prompt_templating": {
>                 "prompt": {
>                     "template": [
>                         {
>                             "role": "user",
>                             "content": "<prompt>\n\nRequest: {{?groundingRequest}}\nReports: {{?groundingOutput}}"
>                         }
>                     ]
>                 },
>                 "model": {
>                     "name": "<modelName>",
>                     "params": {
>                         "max_tokens": 200,
>                         "temperature": 0.2
>                     }
>                 }
>             }
>         }
>     },
>     "placeholder_values": {
>         "groundingRequest": "<grounding query>"
>     }
> }'
> ```

-   **[Contextualized Retrieval Using Metadata and Vector Search](contextualized-retrieval-using-metadata-and-vector-search-911c1ca.md "You can choose to include metadata in the output structure of the grounding module in orchestration. You can leverage the metadata in
    your prompt template.")**  
You can choose to include metadata in the output structure of the grounding module in orchestration. You can leverage the metadata in your prompt template.
-   **[Retrieval Using help.sap.com](retrieval-using-help-sap-com-6c07277.md "
    
    
  ")**  


**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

