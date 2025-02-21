<!-- loio9c972e2301344a5f9511bff4bc7c4fcb -->

# Preparing Data Using the Pipeline API

This API call creates a pipeline for indexing documents.



## Prerequisites

-   You have created a resource group \(see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-6712bfe.md)\).
-   You have created a generic secret \(see [Grounding Generic Secrets for Microsoft SharePoint](grounding-generic-secrets-for-microsoft-sharepoint-bdea357.md)\).



## Context



## Procedure

The following example shows a request using Microsoft SharePoint:

> ### Sample Code:  
> ```
> curl --request POST \
> --url $AI_API_URL/v2/lm/document-grounding/pipelines \
> --header 'AI-Resource-Group: {{resource_group}}' \
> --header 'Content-Type: application/json' \
> --data '{
> 	"type": "MSSharePoint",
> 	"configuration": {
> 		"destination": "<generic secret name>",
> 		"sharePoint": {
> 		"site": {
> 			"name": "<site name>"  // The name of the SharePoint site to be indexed
> 			}
> 		}
> 	}
> }'
> 
> ```

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \
>   --data '{
>   "type": "MSSharePoint",  // Currently, only Microsoft SharePoint is supported
>   "configuration": {
>     "destination": "<generic secret name>",  // Generic secret name created in the previous step
>     "sharePoint": {
>       "site": {
>         "name": "<site name>",  // The name of the SharePoint site to be indexed
>         "includePaths": ["<folder1>", "<folder2>"]  // [Optional] Array of folders within the SharePoint site for selective indexing
>       }
>     }
>   }
> }'
> 
> ```

The `includePaths` is optional. It takes an array of folder paths within the SharePoint site to target for indexing and limits the scope of the pipeline to the specified subfolders or files, meanind that only this content is indexed.





## Next Steps

You can retrieve details of indexing pipelines in the following ways:

-   Get all pipelines

    > ### Sample Code:  
    > ```
    > curl --request GET \  # Use GET method to retrieve all pipelines
    >   --url $AI_API_URL/v2/lm/document-grounding/pipelines \  # URL to fetch all pipelines
    >   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    > 
    > ```

-   Get Pipeline Details by ID

    > ### Sample Code:  
    > ```
    > 
    > curl --request GET \  # Use GET method to retrieve pipeline details by pipeline ID
    >   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}} \  # URL to fetch details of a specific pipeline
    >   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    > 
    > ```

-   Get Pipeline Status by ID

    > ### Sample Code:  
    > ```
    > 
    > curl --request GET \  # Use GET method to check the status of a pipeline
    >   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/status \  # URL to fetch the status of a specific pipeline
    >   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    > 
    > 
    > ```


You can delete pipelines in the following ways:

-   by ID

    > ### Sample Code:  
    > ```
    > curl --request DELETE \  # Use DELETE method to remove a pipeline
    >   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}} \  # URL to delete a specific pipeline by pipeline ID
    >   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    > 
    > ```


