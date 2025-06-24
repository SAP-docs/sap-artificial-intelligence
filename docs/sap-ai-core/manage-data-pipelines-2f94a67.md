<!-- loio2f94a671caa44fe3b7211bd5cb2908d6 -->

# Manage Data Pipelines



<a name="loio2f94a671caa44fe3b7211bd5cb2908d6__section_ubr_qqs_dfc"/>

## Pipelines

You can retrieve details of indexing pipelines in the following ways:

-   Get all pipelines

    > ### Sample Code:  
    > ```
    > curl --request GET \  # Use GET method to retrieve all pipelines
    > --url $AI_API_URL/v2/lm/document-grounding/pipelines\  # URL to fetch all pipelines
    > --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    > 
    > ```

-   Get pipeline details by ID

    > ### Sample Code:  
    > ```
    > 
    > curl --request GET \  # Use GET method to retrieve pipeline details by pipeline ID
    > --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}} \  # URL to fetch details of a specific pipeline
    > --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    > 
    > ```

-   Get pipeline status by ID

    > ### Sample Code:  
    > ```
    > 
    > curl --request GET \  # Use GET method to check the status of a pipeline
    > --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/status \  # URL to fetch the status of a specific pipeline
    > --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    > 
    > 
    > ```


You can delete pipelines by pipeline ID using the following:

> ### Sample Code:  
> ```
> curl --request DELETE \  # Use DELETE method to remove a pipeline
> --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}} \  # URL to delete a specific pipeline by pipeline ID
> --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> 
> ```



<a name="loio2f94a671caa44fe3b7211bd5cb2908d6__section_z4q_rqs_dfc"/>

## Executions

You can list all executions within a pipeline including status details by pipeline ID using the following:

> ### Sample Code:  
> ```
> curl --request GET \  # Use GET method to retrieve all executions of a pipeline
> --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions?lastExecution=false \  # URL to retrieve all executions of a pipeline
> --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
>  
> ```

The `lastExecution` parameter is Boolean, taking `true` or `false` values. Setting the value to `true` will retrieve only the latest execution in the pipeline. Setting the value to `false` will retrieve all executions in the pipeline.

You can get details of an execution including its status by pipeline ID and execution ID using the following:

> ### Sample Code:  
> ```
> curl --request GET \  # Use GET method to retrieve details of specific execution by pipeline ID and execution ID
> --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}} \  # URL to details of specific execution by pipeline ID and execution ID
> --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
>  
> ```



<a name="loio2f94a671caa44fe3b7211bd5cb2908d6__section_xyk_sqs_dfc"/>

## Documents

You can list all documents of an execution including processing statuses by pipeline ID and execution ID using the following:

> ### Sample Code:  
> ```
> curl --request GET \
> --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}}/documents \  # URL to details of specific execution documents by pipeline ID and execution ID
> --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> ```

You can get document details from an execution, including its processing status by pipeline ID, execution ID, and document ID using the following:

> ### Sample Code:  
> ```
> curl --request GET \
> --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}}/documents/{{documentID}} \  # URL to details of specific execution document by pipeline ID, execution ID and Document ID
> --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> ```

You can list all documents within a pipeline including processing statuses by pipeline ID using the following:

> ### Sample Code:  
> ```
> curl --request GET \
> --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/documents \  # URL to details of specific pipeline documents by pipeline ID
> --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> ```

You can get details of a document within a pipeline including its processing status by pipeline ID and document ID using the following:

> ### Sample Code:  
> ```
> curl --request GET \
> --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/documents/{{documentID}} \  # URL to details of specific pipeline document by pipeline ID and Document ID
> --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
> ```

