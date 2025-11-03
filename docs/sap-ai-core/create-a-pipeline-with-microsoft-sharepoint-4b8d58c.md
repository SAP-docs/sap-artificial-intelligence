<!-- copy4b8d58ce4f6a40f0a1cafe9b63ddd38b -->

# Create a Pipeline with Microsoft SharePoint



<a name="copy4b8d58ce4f6a40f0a1cafe9b63ddd38b__section_ljc_ksf_ngc"/>

## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   You have created a generic secret. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).
-   You've added your grounding documents to your document store and you're using a supported data source and document type. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).
-   If you're using metadata, you've configured a metadata server. For more information, see [Prepare your Metadata API Server](prepare-your-metadata-api-server-23a0741.md).



<a name="copy4b8d58ce4f6a40f0a1cafe9b63ddd38b__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines`.




<a name="copy4b8d58ce4f6a40f0a1cafe9b63ddd38b__section_nv3_pcg_ngc"/>

## Without Metadata

The following shows an example of a SharePoint site to be indexed.

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

\{\{resource\_group\}\}

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

\{\{access\_token\}\}

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

<generic secret name\>

</td>
<td valign="top">

The name of the generic secret created for MS SharePoint

</td>
</tr>
<tr>
<td valign="top">

<site name\>

</td>
<td valign="top">

The name of the SharePoint site to be indexed

</td>
</tr>
<tr>
<td valign="top">

\["/<folder1\>", "/<folder2\>/<sub-folder1\>"\]

</td>
<td valign="top">

An array of folders within the SharePoint site for selective indexing \(Optional\)

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \ 
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{
>   "type": "MSSharePoint",
>   "configuration": {
>     "destination": "<generic secret name>",
>     "sharePoint": {
>       "site": {
>         "name": "<site name>",  
>         "includePaths": ["/<folder1>", "/<folder2>/<sub-folder1>"]
>       }
>     }
>   }
> }'
> 
> ```

> ### Note:  
> The `includePaths` parameter is optional. It takes an array of folder paths within the SharePoint site to be indexed and limits the scope of the pipeline to the specified sub folders or files, meaning that only this content is indexed.
> 
> The `includePaths` parameter input is restricted to folder paths within the default document folder of a SharePoint site. No other drives, document library paths, or formats are supported.



<a name="copy4b8d58ce4f6a40f0a1cafe9b63ddd38b__section_v2s_pcg_ngc"/>

## With Metadata

The metadata attribute is optional. It accepts the destination name, which is used to connect to the Microsoft SharePoint metadata server to retrieve metadata for document indexing.

The metadata attribute should be used only if a metadata server is configured. To create a grounding pipeline without metadata, see [Create a Document Grounding Pipeline Using the Pipelines API](create-a-document-grounding-pipeline-using-the-pipelines-api-d32b146.md).

The following shows an example of a SharePoint site to be indexed with metadata.

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

\{\{resource\_group\}\}

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

\{\{access\_token\}\}

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

<generic secret name\> \(destination\)

</td>
<td valign="top">

The name of the generic secret created for Microsoft SharePoint

</td>
</tr>
<tr>
<td valign="top">

<site name\>

</td>
<td valign="top">

The name of the SharePoint site to be indexed

</td>
</tr>
<tr>
<td valign="top">

<generic secret name\> \(metadata\)

</td>
<td valign="top">

The name of the generic secret created for Microsoft SharePoint Metadata Server

</td>
</tr>
</table>

> ### Restriction:  
> `metadata` and `includePaths` cannot be used together in a single payload request.

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \ 
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{
>   "type": "MSSharePoint",
>   "configuration": {
>     "destination": "<generic secret name>",
>     "sharePoint": {
>       "site": {
>         "name": "<site name>"
>       }
>     }
>   },
>   "metadata": {
>     "destination": "<generic secret name>"
>   }
> }'
> ```

To make your pipeline searchable, add `dataRepositoryMetadata` to the `metadata` field. For example:

```
...
    "metadata": {
        "dataRepositoryMetadata": [
            {
                "key": "example",
                "value": [
                    "demo"
                ]
            }
        ]
    }
...
```

For more information, see [Search a Pipeline](search-a-pipeline-5e6727e.md).



## With Scheduled Updates

`cronExpression` is optional. You can add it to your `configuration` to schedule updates to your pipeline, at intervals of your choice.

The following shows an example of a SharePoint site to be indexed at regular intervals.

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

\{\{resource\_group\}\}

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

\{\{access\_token\}\}

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

<generic secret name\>

</td>
<td valign="top">

The name of the generic secret created for MS SharePoint

</td>
</tr>
<tr>
<td valign="top">

<site name\>

</td>
<td valign="top">

The name of the SharePoint site to be indexed

</td>
</tr>
<tr>
<td valign="top">

cronExpression

</td>
<td valign="top">

The cronExpression for the update frequency of your choice \(optional\).

For more information, see [Cron Expressions](cron-expressions-6175008.md).

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \ 
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{
>   "type": "MSSharePoint",
>   "configuration": {
>     "destination": "<generic secret name>", 
>     "cronExpression":"<cron expression>"
>     "sharePoint": {
>       "site": {
>         "name": "<site name>"
>       }
>     }, 
>   }
> }'
> 
> ```

> ### Note:  
> Each repetition of your pipeline is a new deployment, and incurs costs.



<a name="copy4b8d58ce4f6a40f0a1cafe9b63ddd38b__section_c2d_1wg_jgc"/>

## Next Steps

After preparing your vectors, you can use the Retrieval API for chunks relevant to a query, or use the grounding module as part of an orchestration workflow for information retrieval and LLM interaction. For more information, see [Retrieval API](retrieval-api-281e8cf.md) or [Using the Grounding Module](using-the-grounding-module-e1c4dd1.md).

