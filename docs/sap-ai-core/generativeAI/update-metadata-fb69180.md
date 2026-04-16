<!-- loiofb691809c77540848a7d3d6192174295 -->

# Update Metadata



<a name="loiofb691809c77540848a7d3d6192174295__section_ljc_ksf_ngc"/>

## Prerequisites

-   You have created a pipeline using a repository that supports metadata. For more information, see [Create a Document Grounding Pipeline Using the Pipelines API](create-a-document-grounding-pipeline-using-the-pipelines-api-d32b146.md).



## Context

Metadata is additional information associated with data that can help in identifying, categorizing, and retrieving relevant content.You can use your metadata values later to search your pipeline. For more information, see [Search a Pipeline](search-a-pipeline-5e6727e.md).



## Procedure

For repository types that support metadata, you can add or update your metadata by sending a PATCH request to to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}`.

Include the pipeline ID for the pipeline that you want to update.

Ensure that you have the following headers set:


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

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This URL can also be set as an environment variable.

</td>
</tr>
</table>

Metadata organizes information using categories \(keys\) paired with their related values.

> ### Sample Code:  
> ```
> curl --request PATCH \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}} \
>   --header 'ai-resource-group: <resource_group>' \
>   --header 'authorization: Bearer $AUTH_TOKEN' \
>   --header 'content-type: application/json' \
>   --data '{
>   "metadata": {
>     "dataRepositoryMetadata": [
>       {
>         "key": "pipeline/purpose",
>         "value": [
>           "patch-pipeline1"
>         ]
>       },
>       {
>         "key": "pipeline/owner",
>         "value": [
>           "data-engineering",
>           "analytics-team"
>         ]
>       }
>     ]
>   }
> }'
> ```

