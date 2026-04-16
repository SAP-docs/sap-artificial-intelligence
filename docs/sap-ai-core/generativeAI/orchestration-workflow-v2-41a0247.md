<!-- loio41a024780c834de68e070160af93efa5 -->

# Orchestration Workflow V2

In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.



## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get An Orchestration Deployment URL](get-an-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio41a024780c834de68e070160af93efa5__context_a51_5qc_ybc"/>

## Workflow

The order in which the pipeline is executed is defined centrally in orchestration. However, you can configure the details for each module and omit optional modules by passing an orchestration configuration in JSON format with the request body.

> ### Remember:  
> If you're migrating existing orchestration workflows from version 1, you'll need to update your endpoint to `/v2/completion` and modify your existing payloads.

The image shows the orchestration workflow.

![A flow diagram showing the orchestration workflow.](images/orchestration_workflow_v2_9f78b7e.png)



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
>             "max_completion_tokens": 300,
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
>         "providers": [
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



### Example: Output

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



### Example: Output with Citations

For Perplexity Sonar and Sonar Pro models only.

> ### Output Code:  
> ```
> {
>   "request_id": "d62660a7-b1dc-9024-bb89-65371300aac5",
>   "intermediate_results": {
>     "templating": [
>       {
>         "content": "Tell me about SAP Joule.",
>         "role": "user"
>       },
>       {
>         "role": "assistant",
>         "content": "SAP Joule is an AI copilot for business."
>       },
>       {
>         "content": "Analyze the competitive positioning of Perplexity in the AI search market and evaluate how Comet compares to similar offerings from other companies.",
>         "role": "user"
>       }
>     ],
>     "llm": {
>       "id": "5110e37f-9f8e-4be6-a4ae-058a3fb581b7",
>       "object": "chat.completion",
>       "created": 1768208979,
>       "model": "sonar-pro",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "**Perplexity holds a strong but niche position in the AI search market as a leading \"answer engine\" focused on research-oriented, citation-backed queries, processing over 435 million monthly searches and achieving $100 million in annualized revenue by 2025 with a 6.6% market share.[1][2]**\n\n### Market Positioning\nPerplexity differentiates itself as an **AI-native answer engine** built for conversational Q&A, real-time answers, and precise citations using multiple LLMs, outperforming traditional search in benchmarks like SimpleQA (93.9% accuracy, exceeding GPT-4o).[1][2][3] It ranks 7th in AI website popularity (behind ChatGPT, OpenAI, DeepSeek, Gemini, Deepl) with 170 million monthly visits, 30 million daily queries in 2025 (up 20% monthly), and a $18 billion valuation.[1] Key strengths include transparency in sources, fast research (up to 3 minutes vs. competitors' 1.4-2.6 seconds), and appeal to researchers (29% of queries), academics, developers, and content creators (45% usage for fact-checking).[1][3]\n\nLimitations: Less optimized for local/transactional queries; developer adoption lags at 4.9% vs. ChatGPT (81.7%) or Copilot (44.2%); relies on freshness, making it volatile for long-term SEO.[1][3][4]\n\n**Market share and growth**: 6.6% of AI search in October 2025; 500% YoY revenue growth from $20M in 2024; 13.9 million app downloads across 238 countries.[1]\n\n### Competitor Comparison Table\nNo search results mention **Comet** as a comparable AI search offering, so it cannot be evaluated here—possibly a reference to an unindexed tool, internal project, or misspelling (e.g., not matching known players like Consensus or You.com).[3] Below is a comparison of Perplexity to major rivals based on available data:\n\n| Platform          | Type                  | Strengths                          | Limitations                       | Key Metrics (2025)              | Best For                       |\n|-------------------|-----------------------|------------------------------------|-----------------------------------|---------------------------------|-------------------------------|\n| **Perplexity**   | AI-native answer engine | Citations, research focus, multi-LLM | Weaker on local/transactional    | 435M monthly queries, 93.9% SimpleQA[1][3] | Research, fact-checking      |\n| **ChatGPT Search** | Conversational AI    | Deep dialogue, developer tools    | Citations less prominent         | #1 AI site, 81.7% dev usage[1][3] | Generalist, coding           |\n| **Google Gemini/AI Overviews** | AI-enhanced traditional | Query volume dominance, structured data | Less conversational              | Market leader[3][6]            | Everyday, shopping/local     |\n| **Microsoft Copilot (Bing)** | AI-enhanced          | Integrated with Bing               | Manual web search enablement     | 44.2% dev usage[1][3]          | Enterprise, general queries  |\n\nPerplexity excels in credibility for knowledge work but trails volume leaders like Google; AI search splits into native engines (Perplexity leading) vs. enhanced incumbents.[2][3] For 2026, expect Perplexity to grow via API and copilot modes amid rising AI optimization demands like content freshness.[3][4]"
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "prompt_tokens": 44,
>         "completion_tokens": 751,
>         "total_tokens": 795
>       },
>       "citations": [
>         {
>           "ref_id": 1,
>           "title": "60 Perplexity AI Statistics 2026 [Most Important Numbers] - SeoProfy",
>           "url": "https://seoprofy.com/blog/perplexity-ai-statistics/"
>         },
>         {
>           "ref_id": 2,
>           "title": "Perplexity AI Search Engine Deep Dive, What You Need to Know for ...",
>           "url": "https://blueoceanmedia.co.uk/perplexity-ai-search-engine-deep-dive-what-you-need-to-know-for-2026/"
>         },
>         {
>           "ref_id": 3,
>           "title": "AI Search Engines 2026: A Comparison of Perplexity, Google, and ...",
>           "url": "https://aimlapi.com/blog/ai-search-engine"
>         },
>         {
>           "ref_id": 4,
>           "title": "12 Proven Tactics to Rank Higher on Perplexity AI in 2026",
>           "url": "https://nicklafferty.com/blog/how-to-rank-higher-in-perplexity/"
>         },
>         {
>           "ref_id": 5,
>           "title": "Perplexity Finance",
>           "url": "https://www.perplexity.ai/finance"
>         },
>         {
>           "ref_id": 6,
>           "title": "AI Search predictions 2026: From search results to life outcomes",
>           "url": "https://www.adthena.com/resources/blog/ai-search-predictions-2026-from-search-results-to-life-outcomes/"
>         }
>       ]
>     }
>   },
>   "final_result": {
>     "id": "5110e37f-9f8e-4be6-a4ae-058a3fb581b7",
>     "object": "chat.completion",
>     "created": 1768208979,
>     "model": "sonar-pro",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "**Perplexity holds a strong but niche position in the AI search market as a leading \"answer engine\" focused on research-oriented, citation-backed queries, processing over 435 million monthly searches and achieving $100 million in annualized revenue by 2025 with a 6.6% market share.[1][2]**\n\n### Market Positioning\nPerplexity differentiates itself as an **AI-native answer engine** built for conversational Q&A, real-time answers, and precise citations using multiple LLMs, outperforming traditional search in benchmarks like SimpleQA (93.9% accuracy, exceeding GPT-4o).[1][2][3] It ranks 7th in AI website popularity (behind ChatGPT, OpenAI, DeepSeek, Gemini, Deepl) with 170 million monthly visits, 30 million daily queries in 2025 (up 20% monthly), and a $18 billion valuation.[1] Key strengths include transparency in sources, fast research (up to 3 minutes vs. competitors' 1.4-2.6 seconds), and appeal to researchers (29% of queries), academics, developers, and content creators (45% usage for fact-checking).[1][3]\n\nLimitations: Less optimized for local/transactional queries; developer adoption lags at 4.9% vs. ChatGPT (81.7%) or Copilot (44.2%); relies on freshness, making it volatile for long-term SEO.[1][3][4]\n\n**Market share and growth**: 6.6% of AI search in October 2025; 500% YoY revenue growth from $20M in 2024; 13.9 million app downloads across 238 countries.[1]\n\n### Competitor Comparison Table\nNo search results mention **Comet** as a comparable AI search offering, so it cannot be evaluated here—possibly a reference to an unindexed tool, internal project, or misspelling (e.g., not matching known players like Consensus or You.com).[3] Below is a comparison of Perplexity to major rivals based on available data:\n\n| Platform          | Type                  | Strengths                          | Limitations                       | Key Metrics (2025)              | Best For                       |\n|-------------------|-----------------------|------------------------------------|-----------------------------------|---------------------------------|-------------------------------|\n| **Perplexity**   | AI-native answer engine | Citations, research focus, multi-LLM | Weaker on local/transactional    | 435M monthly queries, 93.9% SimpleQA[1][3] | Research, fact-checking      |\n| **ChatGPT Search** | Conversational AI    | Deep dialogue, developer tools    | Citations less prominent         | #1 AI site, 81.7% dev usage[1][3] | Generalist, coding           |\n| **Google Gemini/AI Overviews** | AI-enhanced traditional | Query volume dominance, structured data | Less conversational              | Market leader[3][6]            | Everyday, shopping/local     |\n| **Microsoft Copilot (Bing)** | AI-enhanced          | Integrated with Bing               | Manual web search enablement     | 44.2% dev usage[1][3]          | Enterprise, general queries  |\n\nPerplexity excels in credibility for knowledge work but trails volume leaders like Google; AI search splits into native engines (Perplexity leading) vs. enhanced incumbents.[2][3] For 2026, expect Perplexity to grow via API and copilot modes amid rising AI optimization demands like content freshness.[3][4]"
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "prompt_tokens": 44,
>       "completion_tokens": 751,
>       "total_tokens": 795
>     },
>     "citations": [
>       {
>         "ref_id": 1,
>         "title": "60 Perplexity AI Statistics 2026 [Most Important Numbers] - SeoProfy",
>         "url": "https://seoprofy.com/blog/perplexity-ai-statistics/"
>       },
>       {
>         "ref_id": 2,
>         "title": "Perplexity AI Search Engine Deep Dive, What You Need to Know for ...",
>         "url": "https://blueoceanmedia.co.uk/perplexity-ai-search-engine-deep-dive-what-you-need-to-know-for-2026/"
>       },
>       {
>         "ref_id": 3,
>         "title": "AI Search Engines 2026: A Comparison of Perplexity, Google, and ...",
>         "url": "https://aimlapi.com/blog/ai-search-engine"
>       },
>       {
>         "ref_id": 4,
>         "title": "12 Proven Tactics to Rank Higher on Perplexity AI in 2026",
>         "url": "https://nicklafferty.com/blog/how-to-rank-higher-in-perplexity/"
>       },
>       {
>         "ref_id": 5,
>         "title": "Perplexity Finance",
>         "url": "https://www.perplexity.ai/finance"
>       },
>       {
>         "ref_id": 6,
>         "title": "AI Search predictions 2026: From search results to life outcomes",
>         "url": "https://www.adthena.com/resources/blog/ai-search-predictions-2026-from-search-results-to-life-outcomes/"
>       }
>     ]
>   }
> }
> ```

-   **[Grounding](grounding-035c455.md "The grounding module integrates external, domain-specific, or real-time data into
		generative AI workflows. By enriching pretrained models with contextually relevant
		information, grounding improves response accuracy and relevance beyond the models’ general
		training data.")**  
The grounding module integrates external, domain-specific, or real-time data into generative AI workflows. By enriching pretrained models with contextually relevant information, grounding improves response accuracy and relevance beyond the models’ general training data.
-   **[Templating](templating-3e2ea66.md "")**  

-   **[Translation](translation-29b17df.md "The translation module is optional. It allows you to translate LLM text prompts into a
		chosen target language. ")**  
The translation module is optional. It allows you to translate LLM text prompts into a chosen target language.
-   **[Data Masking](data-masking-d9a54d9.md "The data masking module is optional and serves to anonymize or pseudonymize
		personally identifiable information from the input for selected entities.")**  
The data masking module is optional and serves to anonymize or pseudonymize personally identifiable information from the input for selected entities.
-   **[Content Filtering](content-filtering-f804175.md "")**  


