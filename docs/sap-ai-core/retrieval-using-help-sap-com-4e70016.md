<!-- loio4e70016221d1400dba77d7d40edddac2 -->

# Retrieval Using help.sap.com





<a name="loio4e70016221d1400dba77d7d40edddac2__prereq_pqt_5md_32c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).

You have onboarded a repository. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).



## Context

Meta data inclusion is optional, and can be included using the `metadata_params` field in the completions endpoint of the API. The `metadata_params` field takes a list of comma separated strings.



## Procedure

1.  **Optional:** Retrieve supported metadata keys by sending your query to the endpoint `{{AI_API_Url}}/v2/lm/document-grounding/retrieval/search`.

    > ### Sample Code:  
    > ```
    > curl --request POST \
    >   --url {{AI_API_URL}}/v2/lm/document-grounding/retrieval/search \
    >   --header 'AI-Resource-Group: <resource_group>' \
    >   --header 'Authorization: Bearer <access_token>' \
    >   --header 'Content-Type: application/json' \
    >   --data '{
    >     "query": "what is SAP Joule",
    >     "filters": [
    >         {
    >             "id": "string",
    >             "searchConfiguration": {},
    >             "dataRepositories": [
    >                 "*"
    >             ],
    >             "dataRepositoryType": "help.sap.com",
    >             "documentMetadata": []
    >         }
    >     ],
    >     "documentMetadata": [],
    >     "chunkMetadata": []
    > }'
    > ```

    The response includes details of metadata parameters on the following levels: `dataRepository`,`document` and `chunk`.

2.  To include metadata as part of your request, use `metadata_params` and include them as comma separated strings.

    The following example requests that `source` and `webUrl` metadata is included in the results

    > ### Sample Code:  
    > ```
    > curl --request POST "$ORCH_DEPLOYMENT_URL/completion" \
    > --header "content-type: application/json" \
    > --header "Authorization: Bearer $TOKEN" \
    > --header "ai-resource-group: $RESOURCE_GROUP" \
    > --data-raw '{
    > 	"orchestration_config": {
    > 		"module_configurations": {
    > 			"grounding_module_config": {
    > 				"type": "document_grounding_service",
    > 				"config": {
    > 					"filters": [
    > 						{
    > 							"id": "filter1",
    > 							"data_repositories": [
    > 								"*"
    > 							],
    > 							"search_config": {},
    > 							"data_repository_type": "help.sap.com",
    > 							"document_metadata": []
    > 						}
    > 					]
    > 				}
    > 			},
    > 			"input_params": [
    > 				"groundingRequest",
    > 				"metadata"
    > 			],
    > 			"output_param": "groundingOutput"
    > 		}
    > 	},
    > 	"llm_module_config": {
    > 		"model_name": "<modelName>",
    > 		"model_params": {},
    > 		"model_version": "<modelVersion>"
    > 	},
    > 	"templating_module_config": {
    > 		"template": [
    > 			{
    > 				"role": "user",
    > 				"content": "You are a helpful assistant for any queries for SAP Teched 2024.\nAnswer the grounding request by providing relevant answers that fit to the request. \n\nRequest: {{ ?groundingRequest }}\n\nReports:{{ ?groundingOutput }}"
    > 			}
    > 		],
    > 		"defaults": {}
    > 	},
    > 	"filtering_module_config": {
    > 		"input": {
    > 			"filters": [
    > 				{
    > 					"type": "azure_content_safety",
    > 					"config": {
    > 						"Hate": 2,
    > 						"SelfHarm": 2,
    > 						"Sexual": 2,
    > 						"Violence": 2
    > 					}
    > 				}
    > 			]
    > 		},
    > 		"output": {
    > 			"filters": [
    > 				{
    > 					"type": "azure_content_safety",
    > 					"config": {
    > 						"Hate": 2,
    > 						"SelfHarm": 2,
    > 						"Sexual": 2,
    > 						"Violence": 2
    > 					}
    > 				}
    > 			]
    > 		}
    > 	},
    > 	"input_params": {
    > 		"groundingRequest": "what is SAP Joule?"
    > 	}
    > }'
    > ```


