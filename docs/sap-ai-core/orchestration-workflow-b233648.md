<!-- loiob233648e0696461984410c38448fc81b -->

# Orchestration Workflow

In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.



## Prerequisites

You have a running orchestration deployment. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loiob233648e0696461984410c38448fc81b__context_a51_5qc_ybc"/>

## Workflow

The order in which the pipeline is executed is defined centrally in orchestration. However, you can configure the details for each module and omit optional modules by passing an orchestration configuration in JSON format with the request body.

**The image below is interactive. Click each part of the workflow for more information.**

![](images/4a_orchstration_workflow_2083f88.png)

-   [Grounding](grounding-454c558.md)
-   [Templating](templating-88c5608.md)
-   [Input Translation](input-translation-c43ad1d.md)
-   [Data Masking](data-masking-8b87002.md)
-   [Input Filtering](input-filtering-4446382.md)
-   [Model Configuration](model-configuration-c1bdb26.md)
-   [Output Filtering](output-filtering-b021a5e.md)
-   [Output Translation](output-translation-8f7fb8e.md)



<a name="loiob233648e0696461984410c38448fc81b__section_lt1_n5w_jfc"/>

## Example

This is a sample orchestration request which includes all the above mentioned orchestration modules. In each module section you can find the details of its configuration.

Populate the following variables with your own values:


<table>
<tr>
<th valign="top">

Variable

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

ORCH\_DEPLOYMENT\_URL

</td>
<td valign="top">

Orchestration Deployment URL

</td>
</tr>
<tr>
<td valign="top">

TOKEN

</td>
<td valign="top">

Bearer token generated using SAP AI Core service key

</td>
</tr>
<tr>
<td valign="top">

RESOURCE\_GROUP

</td>
<td valign="top">

The ID of the AI resource group that contains your orchestration deployment

</td>
</tr>
<tr>
<td valign="top">

data\_repositories

</td>
<td valign="top">

Data repository IDs of repositories to be used for document grounding

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $ORCH_DEPLOYMENT_URL/completion \
>   --header "Authorization: Bearer $TOKEN"  \
>   --header "ai-resource-group: $RESOURCE_GROUP"  \
>   --header 'content-type: application/json' \
>   --data '{
>   "orchestration_config": {
>     "module_configurations": {
>       "grounding_module_config": {
>         "type": "document_grounding_service",
>         "config": {
>           "filters": [
>             {
>               "id": "filter1",
>               "data_repositories": [
>                 "<placeholder for data repository ID>"
>               ],
>               "search_config": {
>                 "max_chunk_count": 5
>               },
>               "data_repository_type": "vector"
>             }
>           ],
>           "input_params": ["groundingRequest"],
>           "output_param": "groundingOutput"
>         }
>       },
>       "llm_module_config": {
>         "model_name": "gpt-4o",
>         "model_params": {},
>         "model_version": "latest"
>       },
>       "templating_module_config": {
>         "template": [
>           {
>             "role": "user",
>             "content": "You are a precise and reliable assistant. Using only the provided context, generate a concise and accurate summary relevant to the request. Do not infer or generate information beyond the given context. If the requested information is not available in the context, clearly state that. Request: {{ ?groundingRequest }} Context: {{ ?groundingOutput }}"
>           }
>         ],
>         "defaults": {}
>       },
>       "filtering_module_config": {
>         "input": {
>           "filters": [
>             {
>               "type": "azure_content_safety",
>               "config": {
>                 "Hate": 2,
>                 "SelfHarm": 2,
>                 "Sexual": 2,
>                 "Violence": 2
>               }
>             },
>             {
>               "type": "llama_guard_3_8b",
>               "config": {
>                 "violent_crimes": true,
>                 "non_violent_crimes": true,
>                 "sex_crimes": true,
>                 "child_exploitation": false,
>                 "defamation": false,
>                 "specialized_advice": false,
>                 "privacy": false,
>                 "intellectual_property": false,
>                 "indiscriminate_weapons": false,
>                 "hate": false,
>                 "self_harm": false,
>                 "sexual_content": false,
>                 "elections": false,
>                 "code_interpreter_abuse": false
>               }
>             }
>           ]
>         },
>         "output": {
>           "filters": [
>             {
>               "type": "azure_content_safety",
>               "config": {
>                 "Hate": 2,
>                 "SelfHarm": 2,
>                 "Sexual": 2,
>                 "Violence": 2
>               }
>             }
>           ]
>         }
>       },
>       "masking_module_config": {
>         "masking_providers": [
>           {
>             "type": "sap_data_privacy_integration",
>             "method": "anonymization",
>             "entities": [
>               { "type": "profile-email" },
>               { "type": "profile-person" },
>               { "type": "profile-phone" },
>               { "type": "profile-org" },
>               { "type": "profile-location" }
>             ]
>           }
>         ]
>       },
>       "input_translation_module_config": {
>         "type": "sap_document_translation",
>         "config": {
>           "source_language": "de-DE",
>           "target_language": "en-US"
>         }
>       },
>       "output_translation_module_config": {
>         "type": "sap_document_translation",
>         "config": {
>           "target_language": "de-DE"
>         }
>       }
>     }
>   },
>   "input_params": {
>     "groundingRequest": "Was sind die Schritte zur Ersteinrichtung im SAP AI Core?"
>   }
> }'
> ```

For more information about the modules used in this example, see the following:


<table>
<tr>
<th valign="top">

Orchestration Module

</th>
<th valign="top">

Config

</th>
<th valign="top">

Documentation Link

</th>
</tr>
<tr>
<td valign="top">

Grounding

</td>
<td valign="top">

`grounding_module_config`

</td>
<td valign="top">

[Grounding](grounding-454c558.md)

</td>
</tr>
<tr>
<td valign="top">

Templating \(mandatory\)

</td>
<td valign="top">

`templating_module_config`

</td>
<td valign="top">

[Templating](templating-88c5608.md)

</td>
</tr>
<tr>
<td valign="top">

Model Config \(mandatory\)

</td>
<td valign="top">

`llm_module_config`

</td>
<td valign="top">

[Model Configuration](model-configuration-c1bdb26.md)

</td>
</tr>
<tr>
<td valign="top">

Content Filtering

</td>
<td valign="top">

`filtering_module_config`

</td>
<td valign="top">

[Input Filtering](input-filtering-4446382.md)

[Output Filtering](output-filtering-b021a5e.md)

</td>
</tr>
<tr>
<td valign="top">

Data Masking

</td>
<td valign="top">

`masking_module_config`

</td>
<td valign="top">

[Data Masking](data-masking-8b87002.md)

</td>
</tr>
<tr>
<td valign="top">

Input Translation

</td>
<td valign="top">

`input_translation_module_config`

</td>
<td valign="top">

[Input Translation](input-translation-c43ad1d.md)

</td>
</tr>
<tr>
<td valign="top">

Output Translation

</td>
<td valign="top">

`output_translation_module_config`

</td>
<td valign="top">

[Output Translation](output-translation-8f7fb8e.md)

</td>
</tr>
</table>

> ### Output Code:  
> ```
> {
>   "request_id": "2fa2fd2a-8fb9-9e36-94b8-de17fd1f3e17",
>   "module_results": {
>     "grounding": {
>       "message": "grounding result",
>       "data": {
>         "grounding_query": "grounding call",
>         "grounding_result": "5 Initial Setup\nY ou provision SAP AI Core from the SAP BTP cockpit in SAP Business T echnology Platform. After provisioning,\nyou will have your service key, which provides URLs and credentials for accessing the SAP AI Core instance\nPrerequisites\n our SAP BTP administrator has access to a global account on SAP Business T echnology Platform. For\nmore information, see Getting a Global Account .\n our SAP BTP administrator has set the entitlement to a subaccount.\nContext\nThe SAP AI Core service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone\n(representing the subaccount). The SAP AI Core service instance is created within a subaccount. Each\nsubaccount represents an SAP AI Core tenant.\n  Note\nThe SAP AI Core service does not isolate tenants based on the service instance ID. If you create multiple\nservice instances within the same subaccount, all of them will reference the same SAP AI Core tenant.\n48 PUBLICSAP AI Core\nInitial Setup```The steps below guide you through the provisioning procedure, Alternatively, a booster is available for both\nSAP AI Core and SAP AI Launchpad. For more information, see AI Boosters T utorial\n . If you choose to use the\nbooster, you can skip the remaining steps to SAP AI Core Starter T utorials [page 67] .\n5.1 Enabling the Service in Cloud Foundry\nEnable SAP AI Core using the standard procedures for the SAP BTP Cloud Foundry environment.\nY ou provision SAP AI Core from the SAP BTP cockpit in SAP Business T echnology Platform. After you have\nprovisioned the service, you will have your service key, which provides URLs and credentials for accessing the\nSAP AI Core instance.\nThe SAP AI Core service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone\n(representing the subaccount). The SAP AI Core service instance is created within a subaccount. Each\nsubaccount represents an SAP AI Core tenant.\n  Note```and register your object store for training data and trained models. Productize your\nAI content and expose it as a service to consumers in the SAP BTP marketplace.\nGenerative AI hubChoose from a selection of generative AI models for prompt experimentation, and\nprompt lifecycle management.\nProcess Flow Between SAP AI Core and SAP AI Launchpad\nSAP AI Core\nWhat Is SAP AI Core? PUBLIC 7```5.2 Enabling the Service in the Kyma Environment\nEnable SAP AI Core using the standard procedures for the SAP BTP Kyma environment.\nProcedure\n1. Create a service instance in the Kyma environment.\n2. Y ou can then bind the service instance to your application, or you can create a service key to communicate\ndirectly with the service instance. See Using SAP BTP Services in the Kyma Environment .\nRelated Information\nUsing SAP BTP Services in the Kyma Environment\n66 PUBLICSAP AI Core\nInitial Setup"
>       }
>     },
>     "templating": [
>       {
>         "content": "You are a precise and reliable assistant. Using only the provided context, generate a concise and accurate summary relevant to the request. Do not infer or generate information beyond the given context. If the requested information is not available in the context, clearly state that. Request: Was sind die Schritte zur Ersteinrichtung im SAP AI Core? Context: 5 Initial Setup\nY ou provision SAP AI Core from the SAP BTP cockpit in SAP Business T echnology Platform. After provisioning,\nyou will have your service key, which provides URLs and credentials for accessing the SAP AI Core instance\nPrerequisites\n our SAP BTP administrator has access to a global account on SAP Business T echnology Platform. For\nmore information, see Getting a Global Account .\n our SAP BTP administrator has set the entitlement to a subaccount.\nContext\nThe SAP AI Core service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone\n(representing the subaccount). The SAP AI Core service instance is created within a subaccount. Each\nsubaccount represents an SAP AI Core tenant.\n  Note\nThe SAP AI Core service does not isolate tenants based on the service instance ID. If you create multiple\nservice instances within the same subaccount, all of them will reference the same SAP AI Core tenant.\n48 PUBLICSAP AI Core\nInitial Setup```The steps below guide you through the provisioning procedure, Alternatively, a booster is available for both\nSAP AI Core and SAP AI Launchpad. For more information, see AI Boosters T utorial\n . If you choose to use the\nbooster, you can skip the remaining steps to SAP AI Core Starter T utorials [page 67] .\n5.1 Enabling the Service in Cloud Foundry\nEnable SAP AI Core using the standard procedures for the SAP BTP Cloud Foundry environment.\nY ou provision SAP AI Core from the SAP BTP cockpit in SAP Business T echnology Platform. After you have\nprovisioned the service, you will have your service key, which provides URLs and credentials for accessing the\nSAP AI Core instance.\nThe SAP AI Core service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone\n(representing the subaccount). The SAP AI Core service instance is created within a subaccount. Each\nsubaccount represents an SAP AI Core tenant.\n  Note```and register your object store for training data and trained models. Productize your\nAI content and expose it as a service to consumers in the SAP BTP marketplace.\nGenerative AI hubChoose from a selection of generative AI models for prompt experimentation, and\nprompt lifecycle management.\nProcess Flow Between SAP AI Core and SAP AI Launchpad\nSAP AI Core\nWhat Is SAP AI Core? PUBLIC 7```5.2 Enabling the Service in the Kyma Environment\nEnable SAP AI Core using the standard procedures for the SAP BTP Kyma environment.\nProcedure\n1. Create a service instance in the Kyma environment.\n2. Y ou can then bind the service instance to your application, or you can create a service key to communicate\ndirectly with the service instance. See Using SAP BTP Services in the Kyma Environment .\nRelated Information\nUsing SAP BTP Services in the Kyma Environment\n66 PUBLICSAP AI Core\nInitial Setup",
>         "role": "user"
>       }
>     ],
>     "input_translation": {
>       "message": "Input to LLM is translated successfully.",
>       "data": {
>         "translated_template": "[{\"content\": \"You are a precise and reliable assistant. Using only the provided context, generate a concise and accurate summary relevant to the request. Do not infer or generate information beyond the given context. If the requested information is not available in the context, clearly state that. Request: What are the initial setup steps in the SAP AI Core? Context: 5 Initial Setup\\nY ou commission SAP AI Core from the SAP BTP cockpit in SAP Business T echnology Platform. After provisioning,\\nyou want to have your service key, which provides URLs and credentials for accessing the SAP AI Core instance\\nPrerequisites\\n our SAP BTP administrator has access to a global account on SAP Business T echnology Platform. For\\nmore information, see Getting a Global Account.\\n our SAP BTP administrator has set the entitlement to a subaccount.\\nContext\\nThe SAP AI Core service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone\\n(representing the subaccount). The SAP AI Core service instance is created within a subaccount. Each\\nsubaccount represents to SAP AI Core tenant.\\n Note\\nThe SAP AI Core service does not isolate tenants based on the service instance ID. If you create multiple\\nservice instances within the same subaccount, all of them will reference the same SAP AI Core tenant.\\n48 PUBLICSAP AI Core\\nInitial Setup```The steps below guide you through the provisioning procedure, Alternatively, a booster is available for both\\nSAP AI Core and SAP AI Launchpad. For more information, see AI Boosters T utorial\\n. If you choose to use the\\nbooster, you can skip the remaining steps to SAP AI Core Starter T utorials [page 67].\\n5.1 Enabling the Service in Cloud Foundry\\nEnable SAP AI Core using the standard procedures for the SAP BTP Cloud Foundry environment.\\nY ou provision SAP AI Core from the SAP BTP cockpit in SAP Business T echnology Platform. After you have\\nprovisioned the service, you want to have your service key, which provides URLs and credentials for accessing the\\nSAP AI Core instance.\\nThe SAP AI Core service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone\\n(representing the subaccount). The SAP AI Core service instance is created within a subaccount. Each\\nsubaccount represents to SAP AI Core tenant.\\n Note```and register your object store for training data and trained models. Productize your\\nAI content and expose it as a service to consumers in the SAP BTP marketplace.\\nGenerative AI hubChoose from a selection of generative AI models for prompt experimentation, and\\nprompt lifecycle management.\\nProcess Flow Between SAP AI Core and SAP AI Launchpad\\nSAP AI Core\\nWhat Is SAP AI Core? PUBLIC 7```5.2 Enabling the Service in the Kyma Environment\\nEnable SAP AI Core using the standard procedures for the SAP BTP Kyma environment.\\nProcedure\\n1. Create a service instance in the Kyma environment.\\n2. Y ou can then bind the service instance to your application, or you can create a service key to communicate\\ndirectly with the service instance. See Using SAP BTP Services in the Kyma Environment.\\nRelated Information\\nUsing SAP BTP Services in the Kyma Environment\\n66 PUBLICSAP AI Core\\nInitial Setup\", \"role\": \"user\"}]"
>       }
>     },
>     "input_masking": {
>       "message": "Input to LLM is masked successfully.",
>       "data": {
>         "masked_template": "[{\"content\": \"You are a precise and reliable assistant. Using only the provided context, generate a concise and accurate summary relevant to the request. Do not infer or generate information beyond the given context. If the requested information is not available in the context, clearly state that. Request: What are the initial setup steps in the MASKED_ORG? Context: 5 Initial Setup\\nY ou commission MASKED_ORG from the MASKED_ORG cockpit in MASKED_ORG. After provisioning,\\nyou want to have your service key, which provides URLs and credentials for accessing the MASKED_ORG instance\\nPrerequisites\\n our MASKED_ORG administrator has access to a global account on MASKED_ORG. For\\nmore information, see Getting a Global Account.\\n our MASKED_ORG administrator has set the entitlement to a subaccount.\\nContext\\nThe MASKED_ORG service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone\\n(representing the subaccount). The MASKED_ORG service instance is created within a subaccount. Each\\nsubaccount represents to MASKED_ORG tenant.\\n Note\\nThe MASKED_ORG service does not isolate tenants based on the service instance ID. If you create multiple\\nservice instances within the same subaccount, all of them will reference the same MASKED_ORG tenant.\\n48 MASKED_ORG AI Core\\nInitial Setup```The steps below guide you through the provisioning procedure, Alternatively, a booster is available for both\\nMASKED_ORG and MASKED_ORG Launchpad. For more information, see AI Boosters T utorial\\n. If you choose to use the\\nbooster, you can skip the remaining steps to MASKED_ORG Starter T utorials [page 67].\\n5.1 Enabling the Service in Cloud Foundry\\nEnable MASKED_ORG using the standard procedures for the MASKED_ORG Cloud Foundry environment.\\nY ou provision MASKED_ORG from the MASKED_ORG cockpit in MASKED_ORG. After you have\\nprovisioned the service, you want to have your service key, which provides URLs and credentials for accessing the\\nMASKED_ORG instance.\\nThe MASKED_ORG service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone\\n(representing the subaccount). The MASKED_ORG service instance is created within a subaccount. Each\\nsubaccount represents to MASKED_ORG tenant.\\n Note```and register your object store for training data and trained models. Productize your\\nAI content and expose it as a service to consumers in the MASKED_ORG marketplace.\\nGenerative AI hubChoose from a selection of generative AI models for prompt experimentation, and\\nprompt lifecycle management.\\nProcess Flow Between MASKED_ORG and MASKED_ORG Launchpad\\nMASKED_ORG\\nWhat Is MASKED_ORG? PUBLIC 7```5.2 Enabling the Service in the MASKED_PERSON Environment\\nEnable MASKED_ORG using the standard procedures for the MASKED_ORG MASKED_PERSON environment.\\nProcedure\\n1. Create a service instance in the MASKED_PERSON environment.\\n2. Y ou can then bind the service instance to your application, or you can create a service key to communicate\\ndirectly with the service instance. See Using MASKED_ORG in the MASKED_PERSON Environment.\\nRelated Information\\nUsing MASKED_ORG in the MASKED_PERSON Environment\\n66 MASKED_ORG AI Core\\nInitial Setup\", \"role\": \"user\"}]"
>       }
>     },
>     "input_filtering": {
>       "message": "Input filter passed successfully.",
>       "data": {
>         "azure_content_safety": {
>           "Hate": 0,
>           "SelfHarm": 0,
>           "Sexual": 0,
>           "Violence": 0
>         },
>         "llama_guard_3_8b": {
>           "violent_crimes": false,
>           "non_violent_crimes": false,
>           "sex_crimes": false
>         }
>       }
>     },
>     "llm": {
>       "id": "chatcmpl-BZu6RM8Z1wf74sgGu8gbtwxnoSETM",
>       "object": "chat.completion",
>       "created": 1747896839,
>       "model": "gpt-4o-2024-08-06",
>       "system_fingerprint": "fp_ee1d74bde0",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "The initial setup steps in MASKED_ORG involve:\n\n1. Enabling the service in Cloud Foundry by using standard procedures.\n2. Provisioning MASKED_ORG from the MASKED_ORG cockpit.\n3. Creating a service instance in the MASKED_PERSON environment.\n4. Binding the service instance to your application or creating a service key for direct communication with the service instance."
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 78,
>         "prompt_tokens": 722,
>         "total_tokens": 800
>       }
>     },
>     "output_filtering": {
>       "message": "0 of 1 choices failed the output filter.",
>       "data": {
>         "choices": [
>           {
>             "index": 0,
>             "azure_content_safety": {
>               "Hate": 0,
>               "SelfHarm": 0,
>               "Sexual": 0,
>               "Violence": 0
>             }
>           }
>         ]
>       }
>     },
>     "output_translation": {
>       "message": "Output Translation successful",
>       "data": {
>         "choices": [
>           {
>             "index": 0,
>             "message": {
>               "role": "assistant",
>               "content": "Die Schritte zur Erstkonfiguration in MASKED_ORG umfassen Folgendes:\n\n1. Aktivieren Sie den Service in Cloud Foundry mithilfe von Standardvorgehensweisen.\n2. Bereitstellung von MASKED_ORG aus dem MASKED_ORG-Cockpit.\n3. Anlegen einer Serviceinstanz in der Umgebung MASKED_PERSON.\n4. Binden Sie die Serviceinstanz an Ihre Anwendung, oder legen Sie einen ServiceschlÃ¼ssel fÃ¼r die direkte Kommunikation mit der Serviceinstanz an."
>             },
>             "finish_reason": "stop"
>           }
>         ]
>       }
>     }
>   },
>   "orchestration_result": {
>     "id": "chatcmpl-BZu6RM8Z1wf74sgGu8gbtwxnoSETM",
>     "object": "chat.completion",
>     "created": 1747896839,
>     "model": "gpt-4o-2024-08-06",
>     "system_fingerprint": "fp_ee1d74bde0",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "Die Schritte zur Erstkonfiguration in MASKED_ORG umfassen Folgendes:\n\n1. Aktivieren Sie den Service in Cloud Foundry mithilfe von Standardvorgehensweisen.\n2. Bereitstellung von MASKED_ORG aus dem MASKED_ORG-Cockpit.\n3. Anlegen einer Serviceinstanz in der Umgebung MASKED_PERSON.\n4. Binden Sie die Serviceinstanz an Ihre Anwendung, oder legen Sie einen ServiceschlÃ¼ssel fÃ¼r die direkte Kommunikation mit der Serviceinstanz an."
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 78,
>       "prompt_tokens": 722,
>       "total_tokens": 800
>     }
>   }
> }
> ```

-   **[Grounding](grounding-454c558.md "Grounding integrates external, contextually relevant, domain-specific, or real-time data
		into AI processes. This data enhances the natural language processing capabilities of
		pretrained models, which are trained on general material.")**  
Grounding integrates external, contextually relevant, domain-specific, or real-time data into AI processes. This data enhances the natural language processing capabilities of pretrained models, which are trained on general material.
-   **[Templating](templating-88c5608.md "")**  

-   **[Input Translation](input-translation-c43ad1d.md "")**  

-   **[Data Masking](data-masking-8b87002.md "The data masking module is optional and serves to anonymize or pseudonymize
		personally identifiable information from the input for selected entities.")**  
The data masking module is optional and serves to anonymize or pseudonymize personally identifiable information from the input for selected entities.
-   **[Input Filtering](input-filtering-4446382.md "")**  

-   **[Model Configuration](model-configuration-c1bdb26.md "")**  

-   **[Output Filtering](output-filtering-b021a5e.md "")**  

-   **[Output Translation](output-translation-8f7fb8e.md "")**  


