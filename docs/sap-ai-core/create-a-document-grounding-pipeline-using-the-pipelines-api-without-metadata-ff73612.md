<!-- loioff736128842149afa3bd6a27546b1493 -->

# Create a Document Grounding Pipeline Using the Pipelines API \(without Metadata\)

This API call creates a pipeline for indexing documents for a resource group.



## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   You have created a generic secret. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).
-   You're using a supported data source and document type. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).



<a name="loioff736128842149afa3bd6a27546b1493__section_d3p_kfv_lfc"/>

## Context

> ### Tip:  
> If you use the pipelines API, you do not need to call the Vector API separately. After the data is embedded, you can directly use the Retrieval API to query the vector store for relevant sections.



## Procedure

1.  Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines`.

    **The following examples show requests for each data source:** 




<a name="loioff736128842149afa3bd6a27546b1493__section_hpt_dyx_m2c"/>

## Microsoft SharePoint

The following shows an example of a SharePoint site to be indexed.

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



<a name="loioff736128842149afa3bd6a27546b1493__section_pgh_z2y_m2c"/>

## AWS S3

The following shows an example of an AWS S3 repository to be indexed:

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

\{\{access\_token\}\}

</td>
</tr>
<tr>
<td valign="top">

<generic secret name\>

</td>
<td valign="top">

Name of the generic secret created for AWS S3

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
>   "type": "S3",
>   "configuration": {
>     "destination": "<generic secret name>",
>     "s3": {
>         "includePaths": ["/Sample Files/folder1"]
>     }
>   }
> }'
> ```



<a name="loioff736128842149afa3bd6a27546b1493__section_e1l_cfy_m2c"/>

## SFTP

The following shows an example of an SFTP repository to be indexed:

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

<generic secret name\>

</td>
<td valign="top">

The name of the generic secret created for SFTP

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
>   "type": "SFTP",
>   "configuration": {
>     "destination": "<generic secret name>",
>     "sftp": {
>         "includePaths": ["/Sample Files/folder1"]
>     }
>   }
> }'
> ```



<a name="loioff736128842149afa3bd6a27546b1493__section_wj4_h44_jgc"/>

## SAP Build Work Zone

The following shows an example of a SAP Build Work Zone site to be indexed.

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

The name of the generic secret created for SAP Build Work Zone

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
>   "type": "SAP Build Work Zone",
>   "metadata": {
>     "destination": "<generic secret name>"
>   }
> }'
> ```



<a name="loioff736128842149afa3bd6a27546b1493__section_n1l_212_dgc"/>

## SAP Document Management Service

The following shows an example of a SAP Document Management service site to be indexed.

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

The name of the generic secret created for SAP Document Management service

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
>   "type": "SDM",
>   "metadata": {
>     "destination": "<generic secret name>"
>   }
> }'
> ```



<a name="loioff736128842149afa3bd6a27546b1493__section_c2d_1wg_jgc"/>

## Next Steps

After preparing your vectors, you can use the Retrieval API for chunks relevant to a query, or use the grounding module as part of an orchestration workflow for information retrieval and LLM interaction. For more information, see [Retrieval API](retrieval-api-281e8cf.md) or [Using the Grounding Module](using-the-grounding-module-e1c4dd1.md).

