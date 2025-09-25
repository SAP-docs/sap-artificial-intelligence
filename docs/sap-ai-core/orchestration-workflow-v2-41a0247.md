<!-- loio41a024780c834de68e070160af93efa5 -->

# Orchestration Workflow V2

In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.



## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio41a024780c834de68e070160af93efa5__context_a51_5qc_ybc"/>

## Workflow

The order in which the pipeline is executed is defined centrally in orchestration. However, you can configure the details for each module and omit optional modules by passing an orchestration configuration in JSON format with the request body.

> ### Remember:  
> If you're migrating existing orchestration workflows from version 1, you'll need to update your endpoint to `/v2/completion` and modify your existing payloads.

The image shows the orchestration workflow.

![](images/orchestration_workflow_v2_9f78b7e.png)



<a name="loio41a024780c834de68e070160af93efa5__section_tqj_ty4_vfc"/>

## Using Orchestration

To interact with the orchestration service, send a POST request to your**Orchestration URL**. Ensure that your request includes the appropriate headers and a JSON payload that adheres to the specified schema.

**Base URL**

The base URL is `{{Orchestration URL}}`, and is the URL of your RUNNING orchestration deployment.

**Endpoint**

The endpoint for orchestration v2 is POST `v2/completion`.

Include the following headers in your request:

-   Authorization: Bearer <your-access-token\>
-   content-type: application/json
-   AI-Resource-Group: <your-resource-group\>

**Request Body**

Your request body should follow the following structure:

```
{
    "config": {
    "modules": {
      "prompt_templating": { ...}, // required module
      "<optional module config>": { ...}, // optional modules such as grounding, content filtering etc.
      ...
    }
  },
  "placeholder_values": { ... }
}
```

The templating and model configuration modules are mandatory.

All other modules are optional, and you can choose which to include depending on your use case.

For more information, see the following:


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

`grounding`

</td>
<td valign="top">

[Grounding](grounding-035c455.md)

</td>
</tr>
<tr>
<td valign="top">

Templating \(mandatory\)

</td>
<td valign="top">

`prompt_templating`

</td>
<td valign="top">

[Templating](templating-3e2ea66.md)

</td>
</tr>
<tr>
<td valign="top">

Content Filtering

</td>
<td valign="top">

`filtering`

</td>
<td valign="top">

[Content Filtering](content-filtering-f804175.md) 

</td>
</tr>
<tr>
<td valign="top">

Data Masking

</td>
<td valign="top">

`masking`

</td>
<td valign="top">

[Data Masking](data-masking-d9a54d9.md)

</td>
</tr>
<tr>
<td valign="top">

Translation

</td>
<td valign="top">

`translation`

</td>
<td valign="top">

[Translation](translation-29b17df.md)

</td>
</tr>
</table>



<a name="loio41a024780c834de68e070160af93efa5__section_lt1_n5w_jfc"/>

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
>   --url $ORCH_DEPLOYMENT_URL/v2/completion \
>   --header "Authorization: Bearer $TOKEN"  \
>   --header "AI-Resource-Group: $RESOURCE_GROUP"  \
>   --header 'content-type: application/json' \
>   --data '{
>   "config": {
>     "modules": {
>       "prompt_templating": {
>         "prompt": {
>           "template": [
>             {
>               "role": "assistant",
>               "content": "Support Issue: '''{{?support-issue}}'''\n Context Information: '''{{?issue-context}}'''"
>             },
>             {
>               "role": "system",
>               "content": "You are a helpful support assistant. Your task is to help answer a given support issue. \n Your proceed as follows: \n First, check if the provided context information answers the issue. Based on the result do one of the following: \n a) If yes, provide an answer based on the provided context information in form of an email and then finish. \n b) If no, only if you cannot answer the issue you summarize the issue for the human support team. Ignore the context information in this case and provide your answer only based on the support issue. Answer in the following format:\n - Sentiment: [your sentiment analysis] \n - Key Theme: [theme of the support issue] \n - Contact: [any contact information available in the issue]"
>             }
>           ]
>         },
>         "model": {
>           "name": "gpt-4o",
>           "params": {
>             "max_tokens": 300,
>             "temperature": 0.1,
>             "frequency_penalty": 0,
>             "presence_penalty": 0
>           }
>         }
>       },
>       "filtering": {
>         "input": {
>           "filters": [
>             {
>               "type": "azure_content_safety",
>               "config": {
>                 "hate": 4,
>                 "self_harm": 4,
>                 "sexual": 4,
>                 "violence": 4
>               }
>             }
>           ]
>         },
>         "output": {
>           "filters": [
>             {
>               "type": "azure_content_safety",
>               "config": {
>                 "hate": 0,
>                 "self_harm": 0,
>                 "sexual": 0,
>                 "violence": 0
>               }
>             }
>           ]
>         }
>       },
>       "masking": {
>         "masking_providers": [
>           {
>             "type": "sap_data_privacy_integration",
>             "method": "pseudonymization",
>             "entities": [
>               {
>                 "type": "profile-email"
>               },
>               {
>                 "type": "profile-person"
>               },
>               {
>                 "type": "profile-phone"
>               },
>               {
>                 "type": "profile-address"
>               }
>             ]
>           }
>         ]
>       },
>       "grounding": {
>         "type": "document_grounding_service",
>         "config": {
>           "filters": [
>             {
>               "id": "helpRepo",
>               "data_repositories": [
>                 "*"
>               ],
>               "search_config": {
>                 "max_chunk_count": 3
>               },
>               "data_repository_type": "help.sap.com"
>             }
>           ],
>           "placeholders": {
>             "input": [
>               "support-issue"
>             ],
>             "output": "issue-context"
>           }
>         }
>       },
>       "translation": {
>           "input": {
>               "type": "sap_document_translation",
>               "config": {
>                   "source_language": "de-DE",
>                   "target_language": "en-US"
>               }
>           },
>           "output": {
>               "type": "sap_document_translation",
>               "config": {
>                   "source_language": "en-US",
>                   "target_language": "de-DE"
>               }
>           }
>       }
>     }
>   },
>   "placeholder_values": {
>     "support-issue": "Betreff: Unterstützung benötigt \nNachricht: \nHallo, ich benötige Unterstützung mit SAP Signavio. Insbesondere möchte ich Benachrichtigungen im SAP Signavio Process Manager konfigurieren. Bitte kontaktieren Sie mich mit unter Jane.Janeson@gmx.net."
>   }
> }'
> ```

> ### Output Code:  
> ```
> {
>   "request_id": "527798de-d43b-93ee-b4bd-6111945ae074",
>   "intermediate_results": {
>     "grounding": {
>       "message": "grounding result",
>       "data": {
>         "grounding_query": "grounding call",
>         "grounding_result": "..."
>       }
>     },
>     "templating": [
>       {
>         "role": "assistant",
>         "content": "..."
>       },
>       {
>         "role": "system",
>         "content": "You are a helpful support assistant. Your task is to help answer a given support issue. \n Your proceed as follows: \n First, check if the provided context information answers the issue. Based on the result do one of the following: \n a) If yes, provide an answer based on the provided context information in form of an email and then finish. \n b) If no, only if you cannot answer the issue you summarize the issue for the human support team. Ignore the context information in this case and provide your answer only based on the support issue. Answer in the following format:\n - Sentiment: [your sentiment analysis] \n - Key Theme: [theme of the support issue] \n - Contact: [any contact information available in the issue]"
>       }
>     ],
>     "input_translation": {
>       "message": "Input to LLM is translated successfully.",
>       "data": {
>         "translated_template": "..."
>       }
>     },
>     "input_masking": {
>       "message": "Input to LLM is masked successfully.",
>       "data": {
>         "masked_template": "..."
>       }
>     },
>     "input_filtering": {
>       "message": "Input Filter passed successfully.",
>       "data": {
>         "azure_content_safety": {
>           "Hate": 0,
>           "SelfHarm": 0,
>           "Sexual": 0,
>           "Violence": 0
>         }
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
>               "content": "E-Mail-Antwort: Betreff: Unterstützung beim Konfigurieren von Benachrichtigungen in SAP Signavio Process Manager Sehr geehrter Benutzer, vielen Dank, dass Sie sich bezüglich Ihrer Anfrage bezüglich der Konfiguration von Benachrichtigungen in SAP Signavio Process Manager an uns gewendet haben.  Um Ihre Benachrichtigungseinstellungen anzupassen, führen Sie die folgenden Schritte aus: 1. **Benachrichtigungen für ein bestimmtes Diagramm deaktivieren:** – Diagramm im Explorer auswählen.- Öffnen Sie den Aktivitäts-Feed, indem Sie die Leertaste drücken..- Wählen Sie \"Keine Benachrichtigung\", um keine Benachrichtigungen über Änderungen an diesem Diagramm mehr zu erhalten. 2. **Globale Benachrichtigungseinstellungen anpassen:** - Navigieren Sie zu Ihren Profileinstellungen, indem Sie im Explorer Setup - Mein Profil wählen..- Blättern Sie nach unten zum Abschnitt für die Benachrichtigungseinstellungen..- Hier können Sie Ihre Benachrichtigungsvoreinstellungen Ihren Anforderungen entsprechend anpassen.  Wenn Sie weitere Unterstützung benötigen oder zusätzliche Fragen haben, können Sie sich jederzeit an uns wenden.  Mit freundlichen Grüßen [Ihr Supportteam]"
>             },
>             "finish_reason": "stop"
>           }
>         ]
>       }
>     },
>     "llm": {
>       "id": "chatcmpl-BtyoOcoO9vPl1IbBZVyYtIOkUJaGJ",
>       "object": "chat.completion",
>       "created": 1752681500,
>       "model": "gpt-4o-2024-08-06",
>       "system_fingerprint": "fp_ee1d74bde0",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "Email Response:\n\nSubject: Assistance with Configuring Notifications in SAP Signavio Process Manager\n\nDear User,\n\nThank you for reaching out to us regarding your query on configuring notifications in SAP Signavio Process Manager.\n\nTo adjust your notification settings, please follow these steps:\n\n1. **Disable Notifications for a Specific Diagram:**\n   - Select the diagram in the Explorer.\n   - Open the activity feed by pressing the space bar.\n   - Choose \"Don't notify me\" to stop receiving notifications for changes made to that diagram.\n\n2. **Adjust Global Notification Settings:**\n   - Navigate to your profile settings by selecting Setup - My profile in the Explorer.\n   - Scroll down to the notification settings section.\n   - Here, you can customize your notification preferences according to your needs.\n\nIf you need further assistance or have additional questions, please feel free to reach out to us at your convenience.\n\nBest regards,\n\n[Your Support Team]"
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 196,
>         "prompt_tokens": 1621,
>         "total_tokens": 1817
>       }
>     }
>   },
>   "final_result": {
>     "id": "chatcmpl-BtyoOcoO9vPl1IbBZVyYtIOkUJaGJ",
>     "object": "chat.completion",
>     "created": 1752681500,
>     "model": "gpt-4o-2024-08-06",
>     "system_fingerprint": "fp_ee1d74bde0",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "E-Mail-Antwort: Betreff: Unterstützung beim Konfigurieren von Benachrichtigungen in SAP Signavio Process Manager Sehr geehrter Benutzer, vielen Dank, dass Sie sich bezüglich Ihrer Anfrage bezüglich der Konfiguration von Benachrichtigungen in SAP Signavio Process Manager an uns gewendet haben.  Um Ihre Benachrichtigungseinstellungen anzupassen, führen Sie die folgenden Schritte aus: 1. **Benachrichtigungen für ein bestimmtes Diagramm deaktivieren:** – Diagramm im Explorer auswählen.- Öffnen Sie den Aktivitäts-Feed, indem Sie die Leertaste drücken..- Wählen Sie \"Keine Benachrichtigung\", um keine Benachrichtigungen über Änderungen an diesem Diagramm mehr zu erhalten. 2. **Globale Benachrichtigungseinstellungen anpassen:** - Navigieren Sie zu Ihren Profileinstellungen, indem Sie im Explorer Setup - Mein Profil wählen..- Blättern Sie nach unten zum Abschnitt für die Benachrichtigungseinstellungen..- Hier können Sie Ihre Benachrichtigungsvoreinstellungen Ihren Anforderungen entsprechend anpassen.  Wenn Sie weitere Unterstützung benötigen oder zusätzliche Fragen haben, können Sie sich jederzeit an uns wenden.  Mit freundlichen Grüßen [Ihr Supportteam]"
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 196,
>       "prompt_tokens": 1621,
>       "total_tokens": 1817
>     }
>   }
> }
> ```

-   **[Grounding](grounding-035c455.md "Grounding integrates external, contextually relevant, domain-specific, or real-time data
		into AI processes. This data enhances the natural language processing capabilities of
		pretrained models, which are trained on general material.")**  
Grounding integrates external, contextually relevant, domain-specific, or real-time data into AI processes. This data enhances the natural language processing capabilities of pretrained models, which are trained on general material.
-   **[Templating](templating-3e2ea66.md "")**  

-   **[Translation](translation-29b17df.md "")**  

-   **[Data Masking](data-masking-d9a54d9.md "The data masking module is optional and serves to anonymize or pseudonymize
		personally identifiable information from the input for selected entities.")**  
The data masking module is optional and serves to anonymize or pseudonymize personally identifiable information from the input for selected entities.
-   **[Content Filtering](content-filtering-f804175.md "")**  


