<!-- copya8d271609bb84fbf9a441fb25501815e -->

# Create a Pipeline with Google Drive

Creates a document grounding pipeline that indexes content from Google Drive using a generic secret, with optional metadata and scheduled updates.



<a name="copya8d271609bb84fbf9a441fb25501815e__section_ljc_ksf_ngc"/>

## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   The generic secret for Google Drive is available. For more information, see [Create a Generic Secret for Google Drive](create-a-generic-secret-for-google-drive-99582a7.md).
-   You have created a generic secret for Google Drive. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).
-   You have added your grounding documents to Google Drive using a supported document type. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).
-   If you are using metadata, you have configured a metadata server. For more information, see [Prepare your Metadata API Server](prepare-your-metadata-api-server-23a0741.md).



<a name="copya8d271609bb84fbf9a441fb25501815e__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines`.




<a name="copya8d271609bb84fbf9a441fb25501815e__section_nv3_pcg_ngc"/>

## Without Metadata

The following shows an example of a Google Drive resource to be indexed.

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

`{{resource_group}}`

</td>
<td valign="top">

The AI resource group assigned to your account

</td>
</tr>
<tr>
<td valign="top">

`$AI_API_URL`

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable

</td>
</tr>
<tr>
<td valign="top">

`{{access_token}}`

</td>
<td valign="top">

Your access token for SAP AI Core  

</td>
</tr>
<tr>
<td valign="top">

`<generic secret name>`

</td>
<td valign="top">

The name of the generic secret created for Google Drive

</td>
</tr>
<tr>
<td valign="top">

`<resource id>`

</td>
<td valign="top">

The ID of the shared drive or shared folder

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> curl --request POST \
>   --url "$AI_API_URL/v2/lm/document-grounding/pipelines" \
>   --header "AI-Resource-Group: <resource-group>" \
>   --header "Content-Type: application/json" \
>   --header "Authorization: Bearer $TOKEN" \
>   --data '{
>     "type": "GoogleDrive",
>     "configuration": {
>       "destination": "<GENERIC_SECRET_NAME>",
>       "googleDrive": {
>         "resourceType": "<SHARED_DRIVE_OR_SHARED_FOLDER>",
>         "resourceId": "<SHARED_DRIVE_ID_OR_SHARED_FOLDER_ID>",
>         "includePaths": [
>           "path/to/folder1",
>           "path/to/folder2"
>         ]
>       }
>     }
>   }'
> 
> 
>             
> ```



<a name="copya8d271609bb84fbf9a441fb25501815e__section_v2s_pcg_ngc"/>

## With Metadata

Metadata is additional information associated with data that can help in identifying, categorizing, and retrieving relevant content. 

> ### Tip:  
> Alternatively, you can create a reusable metadata configurations and then reference your configuration when creating your pipeline. For more information, see [Create a Metadata Configuration](create-a-metadata-configuration-51a3fe1.md) and [Create a Pipeline using a Metadata Configuration](create-a-pipeline-using-a-metadata-configuration-454abf5.md).

The metadata attribute is optional and must be used only if a metadata server is configured. To create a pipeline without metadata, see [Create a Document Grounding Pipeline Using the Pipelines API](create-a-document-grounding-pipeline-using-the-pipelines-api-d32b146.md).

> ### Sample Code:  
> ```
> 
> 
> curl --request POST \
>   --url "$AI_API_URL/v2/lm/document-grounding/pipelines" \
>   --header "AI-Resource-Group: <resource-group>" \
>   --header "Content-Type: application/json" \
>   --header "Authorization: Bearer $TOKEN" \
>   --data '{
>     "type": "GoogleDrive",
>     "configuration": {
>       "destination": "<GENERIC_SECRET_NAME>",
>       "googleDrive": {
>         "resourceType": "<SHARED_DRIVE_OR_SHARED_FOLDER>",
>         "resourceId": "<SHARED_DRIVE_ID_OR_SHARED_FOLDER_ID>"
>       }
>     },
>     "metadata": {
>       "destination": "<METADATA_SECRET_NAME>"
>     }
>   }'
> 
>             
> ```



## With Scheduled Updates

`cronExpression` is optional. You can add it to your `configuration` to schedule pipeline updates at intervals of your choice.

> ### Sample Code:  
> ```
> 
> curl --request POST \
>   --url "$AI_API_URL/v2/lm/document-grounding/pipelines" \
>   --header "AI-Resource-Group: <resource-group>" \
>   --header "Content-Type: application/json" \
>   --header "Authorization: Bearer $TOKEN" \
>   --data '{
>     "type": "GoogleDrive",
>     "configuration": {
>       "destination": "<GEN>",
>       "googleDrive": {
>         "resourceType": "<SHARED_DRIVE_OR_SHARED_FOLDER>",
>         "resourceId": "<SHARED_DRIVE_ID_OR_SHARED_FOLDER_ID>"
>       },
>       "cronExpression": "<CRON_EXPRESSION>"
>     }
>   }'
> 
> 
> ```



## Pipeline Configuration Options

Google Drive pipelines support two resource types and an optional auto-discovery mode.

**Parameters**

-   `resourceType`: Specifies the Google Drive resource type. Valid values are `SHARED_FOLDER` and `SHARED_DRIVE`.
-   `resourceId`: Specifies the unique ID of the Google Drive folder or shared drive. If this parameter is omitted, auto-discovery mode is enabled and the pipeline scans all resources shared with the service account.
-   `includePaths`: Specifies an array of strings to filter specific sub-folders. Example: `["ProjectDocs/Final"]`.

> ### Note:  
> If `resourceId` is not specified, the pipeline runs in auto-discovery mode and retrieves all files that the service account has permission to read.



<a name="copya8d271609bb84fbf9a441fb25501815e__section_c2d_1wg_jgc"/>

## Next Steps

After preparing your vectors, you can use the Retrieval API for chunks relevant to a query, or use the grounding module as part of an orchestration workflow for information retrieval and LLM interaction. For more information, see [Retrieval API](retrieval-api-281e8cf.md) or [Using the Grounding Module](using-the-grounding-module-e1c4dd1.md).

You can add metadata to your pipeline, or update existing metadata by sending a patch request. For more information, see [Update Metadata](update-metadata-fb69180.md).



## Supported File Types

The Google Drive pipeline supports common document and image file types. Google Workspace native formats are handled by remapping supported files to equivalent Microsoft Office formats. Unsupported file types are skipped during pipeline execution.

Supported file types:

-   DOCX
-   HTML \(static\)
-   JPEG
-   JPG
-   JSON
-   PDF
-   PNG
-   PPTX
-   TIFF
-   TXT

Google Drive-specific file types:

-   Google Docs \(`.gdoc`\) are remapped to `.docx`.
-   Google Slides \(`.gslides`\) are remapped to `.pptx`.

Unsupported file types:

-   Other Google Workspace formats, such as Google Sheets
-   Other file formats, such as `.xlsx`

