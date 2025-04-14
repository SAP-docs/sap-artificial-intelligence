<!-- loio2f94a671caa44fe3b7211bd5cb2908d6 -->

# Manage Data Pipelines

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


You can get the list of all the executions with status for any pipeline in the following ways:

-   by pipeline ID

    > ### Sample Code:  
    > ```
    > curl --request GET \  # Use GET method to retrieve all executions of a pipeline
    >   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions?lastExecution=false \  # URL to retrieve all executions of a pipeline
    >   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    >  
    > ```


You can get details of any execution including it's status in the following ways:

-   by pipeline ID and execution ID

    > ### Sample Code:  
    > ```
    > curl --request GET \  # Use GET method to retrieve details of specific execution by pipeline ID and execution ID
    >   --url $AI_API_URL/v2/lm/document-grounding/pipelines/{{pipelineId}}/executions/{{executionId}} \  # URL to details of specific execution by pipeline ID and execution ID
    >   --header 'AI-Resource-Group: {{resource_group}}'  # Add the resource group ID in the header
    >  
    > ```


