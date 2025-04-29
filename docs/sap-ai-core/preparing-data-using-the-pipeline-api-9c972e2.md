<!-- loio9c972e2301344a5f9511bff4bc7c4fcb -->

# Preparing Data Using the Pipeline API

This API call creates a pipeline for indexing documents.



## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-6712bfe.md).
-   You have created a generic secret. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-fbf4dae.md).



## Procedure

Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines`.

The following examples show requests for each repository type:



<a name="concept_hpt_dyx_m2c"/>

<!-- concept\_hpt\_dyx\_m2c -->

## Microsoft SharePoint



The following shows an example of a SharePoint site to be indexed:

> ### Sample Code:  
> ```
> curl --request POST \
> --url $AI_API_URL/v2/lm/document-grounding/pipelines \
> --header 'AI-Resource-Group: {{resource_group}}' \
> --header 'Content-Type: application/json' \
> --data '{
> 	"type": "MSSharePoint",
> 	"configuration": {
> 		"destination": "<generic secret name>", // The name of the generic secret created for MS SharePoint
> 		"sharePoint": {
> 			"site": {
> 				"name": "<site name>"  // The name of the MS SharePoint site to be indexed
> 			}
> 		}
> 	}
> }'
> 
> ```

The following shows an example of a specific folders to be indexed:

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \
>   --data '{
>   "type": "MSSharePoint",  // 
>   "configuration": {
>     "destination": "<generic secret name>",  // The name of the generic secret created for MS SharePoint
>     "sharePoint": {
>       "site": {
>         "name": "<site name>",  // The name of the SharePoint site to be indexed
>         "includePaths": ["/<folder1>", "/<folder2>/<sub-folder1>"]  // [Optional] Array of folders within the SharePoint site for selective indexing
>       }
>     }
>   }
> }'
> 
> ```

> ### Note:  
> The `includePaths` parameter is optional. It takes an array of folder paths within the SharePoint site to be indexed and limits the scope of the pipeline to the specified sub folders or files, meaning that only this content is indexed.
> 
> The `includePaths` parameter input is restricted to folder paths within the default document folder of a SharePoint site.. No other drives, document library paths, or formats are supported.

The following shows an example of a specific folders to be indexed with metadata:

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \
>   --data '{
>   "type": "MSSharePoint",
>   "configuration": {
>     "destination": "<generic secret name>",  // The name of the generic secret created for MS SharePoint
>     "sharePoint": {
>       "site": {
>         "name": "<site name>",  // The name of the SharePoint site to be indexed
>       }
>     }
>   },
>   "metadata": {
>     "destination": "<generic secret name>",  // Name of the generic secret created for MSSharePoint MetaData Server
>   }
> }'
> ```

The metadata attribute is optional. It accepts the destination name, which is used to connect to the Microsoft SharePoint metadata server to retrieve metadata for document indexing.

> ### Restriction:  
> `metadata` and `includePaths` cannot be used together in a single payload request.

<a name="concept_pgh_z2y_m2c"/>

<!-- concept\_pgh\_z2y\_m2c -->

## AWS S3



The following shows an example of an AWS S3 repository to be indexed:

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \
>   --data '{
>   "type": "S3",
>   "configuration": {
>     "destination": "<generic secret name>"  // Name of the generic secret created for S3
>   }
> }'
> ```

The following shows an example of an AWS S3 repository to be indexed with metadata:

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \
>   --data '{
>   "type": "S3",
>   "configuration": {
>     "destination": "<generic secret name>"  // Name of the generic secret created for S3
>   },
>   "metadata": {
>     "destination": "<generic secret name>",  // Name of the generic secret created for S3 MetaData Server
>   }
> }'
> ```

The metadata attribute is optional. It accepts the destination name, which is used to connect to the AWS S3 metadata server to retrieve metadata for document indexing.

<a name="concept_e1l_cfy_m2c"/>

<!-- concept\_e1l\_cfy\_m2c -->

## SFTP



The following shows an example of an SFTP repository to be indexed:

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \
>   --data '{
>   "type": "SFTP",
>   "configuration": {
>     "destination": "<generic secret name>"  // Name of the generic secret created for SFTP
>   }
> }'
> ```

The following shows an example of an SFTP repository to be indexed with metadata:

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \
>   --data '{
>   "type": "SFTP",
>   "configuration": {
>     "destination": "<generic secret name>"  // Name of the generic secret created for SFTP
>   },
>   "metadata": {
>     "destination": "<generic secret name>",  // Name of the generic secret created for SFTP MetaData Server
>   }
> }'
> ```

The metadata attribute is optional. It accepts the destination name, which is used to connect to the SFTP metadata server to retrieve metadata for document indexing.

