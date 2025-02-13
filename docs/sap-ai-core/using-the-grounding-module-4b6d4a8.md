<!-- loio4b6d4a8a43dd4eb88be5f087efaddd92 -->

# Using the Grounding Module



<a name="loio4b6d4a8a43dd4eb88be5f087efaddd92__section_vr2_rpj_12c"/>

## Prerequisites

You have created a deployment for orchestration as described at [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio4b6d4a8a43dd4eb88be5f087efaddd92__section_iq5_rpj_12c"/>

## Process

The following code illustrates how you can use the grounding module with SAP HANA Vector Store.

> ### Sample Code:  
> ```
> curl --request POST $ORCH_DEPLOYMENT_URL/completion \
> --header 'content-type: application/json' \
> --header "Authorization: Bearer $TOKEN" \
> --header "ai-resource-group: $RESOURCE_GROUP" \
> --data-raw '{
>   "orchestration_config": {
>     "module_configurations": {
>       "grounding_module_config": {  // Configuration for the document grounding module
>         "type": "document_grounding_service",  // Specifies the module type as a grounding service
>         "config": {
>           "filters": [  // Define the filters to apply during the grounding process
>             {
>               "id": "filter",  // Filter identifier
>               "data_repositories": [  // Specifies which repositories to use for document grounding
>                 "*"  // Use all available data repositories
>               ],
>               "search_config": {  // Configuration related to search functionality
>                 "max_chunk_count": 10  // Limits the maximum number of chunks to retrieve
>               },
>               "data_repository_type": "vector"  // Defines the type of data repository (vector-based in this case)
>             }
>           ],
>           "input_params": [
>             "groundingRequest"  // Input parameter, typically the query or grounding request
>           ],
>           "output_param": "groundingOutput"  // Output parameter where the grounding results will be stored
>         }
>       },
>       "llm_module_config": {  // Configuration for the Large Language Model (LLM) module
>         "model_name": "gemini-1.5-pro",  // Name of the model to use for processing (Gemini 1.5 Pro)
>         "model_params": {},  // Parameters for the LLM model, left empty for default behavior
>         "model_version": "001"  // Version of the LLM model being used
>       },
>       "templating_module_config": {  // Configuration for the templating module
>         "template": [
>           {
>             "role": "user",  // Role within the conversation template, e.g., user or assistant
>             "content": "<prompt>"  // Content placeholder for the user prompt
>           }
>         ],
>         "defaults": {}  // Default settings for the templating module, currently empty
>       }
>     }
>   },
>   "input_params": {
>     "groundingRequest": "<grounding query>"  // The input parameter containing the grounding query
>   },
>   "return_module_results": true  // Return results from each module used in the orchestration
> }
> 
> ```

-   **[Metadata](metadata-9913885.md "You can choose to include metadata in the output structure of the grounding module in orchestration. You can leverage the metadata in your
		prompt template.")**  
You can choose to include metadata in the output structure of the grounding module in orchestration. You can leverage the metadata in your prompt template.

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

