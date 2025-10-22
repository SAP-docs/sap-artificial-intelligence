<!-- copyc272711c50034681a1f7bf1beb206b19 -->

# Create a Document Grounding Pipeline Using the Pipelines API \(with Metadata\)

This API call creates a pipeline for indexing documents for a resource group.



## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   You have created a generic secret. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).
-   You're using a supported data source and document type. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).



<a name="copyc272711c50034681a1f7bf1beb206b19__section_d3p_kfv_lfc"/>

## Context

The metadata attribute should be used only if a metadata server is configured. To create a grounding pipeline without metadata, see [Create a Document Grounding Pipeline Using the Pipelines API \(without Metadata\)](create-a-document-grounding-pipeline-using-the-pipelines-api-without-metadata-ff73612.md).

> ### Tip:  
> If you use the pipelines API, you do not need to call the Vector API separately. After the data is embedded, you can directly use the Retrieval API to query the vector store for relevant sections.



## Procedure

1.  Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines`.

    **The following examples show requests for each data source:**




<a name="copyc272711c50034681a1f7bf1beb206b19__section_hpt_dyx_m2c"/>

## Microsoft SharePoint

The following shows an example of a SharePoint site to be indexed with metadata.

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

 

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

The name of the generic secret created for Microsoft SharePoint MetaData Server

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

The metadata attribute is optional. It accepts the destination name, which is used to connect to the Microsoft SharePoint metadata server to retrieve metadata for document indexing.

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



<a name="copyc272711c50034681a1f7bf1beb206b19__section_pgh_z2y_m2c"/>

## AWS S3

The following shows an example of an AWS S3 repository to be indexed with metadata:

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

 

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

<generic secret name\> \(configuation\)

</td>
<td valign="top">

The name of the generic secret created for AWS S3

</td>
</tr>
<tr>
<td valign="top">

<generic secret name\> \(metadata\)

</td>
<td valign="top">

The name of the generic secret created for the AWS S3 MetaData Server

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
>   "type": "S3",
>   "configuration": {
>    "destination": "<generic secret name>",
>     "s3": {
>         "includePaths": ["/Sample Files/folder1"]
>     }
>   },
>   "metadata": {
>     "destination": "<generic secret name>"
>   }
> }'
> ```

The metadata attribute is optional. It accepts the destination name, which is used to connect to the AWS S3 metadata server to retrieve metadata for document indexing.

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



<a name="copyc272711c50034681a1f7bf1beb206b19__section_e1l_cfy_m2c"/>

## SFTP

The following shows an example of an SFTP repository to be indexed with metadata:

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

 

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

<generic secret name\> \(configuation\)

</td>
<td valign="top">

The name of the generic secret created for SFTP

</td>
</tr>
<tr>
<td valign="top">

<generic secret name\> \(metadata\)

</td>
<td valign="top">

The name of the generic secret created for the SFTP MetaData Server

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
>   "type": "SFTP",
>   "configuration": {
>     "destination": "<generic secret name>",
>     "sftp": {
>         "includePaths": ["/Sample Files/folder1"]
>     },
>   "metadata": {
>     "destination": "<generic secret name>"
>   }
> }'
> ```

The metadata attribute is optional. It accepts the destination name, which is used to connect to the SFTP metadata server to retrieve metadata for document indexing.

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



<a name="copyc272711c50034681a1f7bf1beb206b19__section_c2d_1wg_jgc"/>

## Next Steps

After preparing your vectors, you can use the Retrieval API for chunks relevant to a query, or use the grounding module as part of an orchestration workflow for information retrieval and LLM interaction. For more information, see [Retrieval API](retrieval-api-281e8cf.md) or [Using the Grounding Module](using-the-grounding-module-e1c4dd1.md).

