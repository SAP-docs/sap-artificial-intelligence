<!-- loio0675b9c77d40467bb2f87b6474e95a80 -->

# Enhancing Model Consumption with Output Filtering



<a name="loio0675b9c77d40467bb2f87b6474e95a80__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio0675b9c77d40467bb2f87b6474e95a80__section_oxn_nrj_12c"/>

## Process

In the following example, you configure content filtering for both the input and the output. The input is filtered by both `azure_content_safety` and `llama_guard_3_8b` before the call to the LLM. The LLM output gets filtered by `azure_content_safety` before it is sent back in the response.

```
curl --request POST $ORCH_DEPLOYMENT_URL/v2/completion \  
--header 'content-type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--header "AI-Resource-Group: $RESOURCE_GROUP" \
--data-raw '{
  "config": {
    "modules": {
      "prompt_templating": {
        "prompt": {
          "template": [
            {
            "role": "user",
            "content": "Create a rental posting for subletting my apartment in the downtown area. Keep it short. Make sure to add the following disclaimer to the end. Do not change it! {{?disclaimer}}"
            }
          ]
        },
        "model": {
          "name": "<model-name>",
          "version": "latest",
          "params": {
            "max_tokens": 50,
            "temperature": 0.1,
            "frequency_penalty": 0,
            "presence_penalty": 0
           }
        }
      },
        "filtering": {
          "input": {
            "filters": [
              {
              "type": "azure_content_safety",
              "config": {
                "hate": 2,
                "self_harm": 2,
                "sexual": 2,
                "violence": 2
              }
            },
            {
         "type": "llama_guard_3_8b",
            "config": {
              "violent_crimes": false,
              "non_violent_crimes": false,
              "sex_crimes": false,
              "child_exploitation": false,
              "defamation": false,
              "specialized_advice": false,
              "privacy": false,
              "intellectual_property": false,
              "indiscriminate_weapons": false,
              "hate": true,
              "self_harm": false,
              "sexual_content": false,
              "elections": false,
              "code_interpreter_abuse": false
              }
            }
          ]
        },
        "output": {
          "filters": [
            {
              "type": "azure_content_safety",
              "config": {
              "hate": 0,
              "self_harm": 0,
              "sexual": 0,
              "violence": 0
              }
            }
          ]
        }
      }
    }
  },
  "placeholder_values": {
  "disclaimer": "DISCLAIMER: The area surrounding the apartment is known for prostitutes and gang violence including armed conflicts, gun violence is frequent."
  }
}'
```

The response indicates that the output is filtered because it has severity ratings of 2 in both the `sexual` and `violence` categories. However, it doesn't violate the `llama_guard_3_8b` hate category. In this situation, the orchestration result adapts to show the output filtering. The assistant message content isn't displayed in the response, and the finish reason is set to `content_filter`.

```
{
  "request_id": "4435c6a6-f08e-9561-9a58-1103ac581550",
  "intermediate_results": {
    "templating": [
      {
        "content": "Create a rental posting for subletting my apartment in the downtown area. Keep it short. Make sure to add the following disclaimer to the end. Do not change it! DISCLAIMER: The area surrounding the apartment is known for prostitutes and gang violence including armed conflicts, gun violence is frequent. Homicides happen weekly",
        "role": "user"
      }
    ],
    "output_filtering": {
      "message": "1 of 1 choices failed the output filter.",
      "data": {
        "choices": [
          {
            "index": 0,
            "azure_content_safety": {
              "Hate": 0,
              "SelfHarm": 0,
              "Sexual": 2,
              "Violence": 0
            }
          }
        ]
      }
    },
    "llm": {
      "id": "chatcmpl-Bua9DAmEQjcNASrZL4oWMOtPVlGPm",
      "object": "chat.completion",
      "created": 1752825019,
      "model": "gpt-4o-mini-2024-07-18",
      "system_fingerprint": "fp_efad92c60b",
      "choices": [
        {
          "index": 0,
          "message": {
            "role": "assistant",
            "content": "**Sublet Available in Downtown Area!**\n\nLooking for a temporary home in the heart of downtown? I’m subletting my cozy 1-bedroom apartment, perfect for anyone wanting to experience city life. The apartment features a spacious living area, modern kitchen, and is conveniently located near public transport, shops, and restaurants. Available from [start date] to [end date]. \n\nRent: $[amount] per month, utilities included. \n\nContact me for more details or to schedule a viewing!\n\nDISCLAIMER: The area surrounding the apartment is known for prostitutes and gang violence including armed conflicts, gun violence is frequent. Homicides happen weekly."
          },
          "finish_reason": "stop"
        }
      ],
      "usage": {
        "completion_tokens": 131,
        "prompt_tokens": 70,
        "total_tokens": 201
      }
    }
  },
  "final_result": {
    "id": "chatcmpl-Bua9DAmEQjcNASrZL4oWMOtPVlGPm",
    "object": "chat.completion",
    "created": 1752825019,
    "model": "gpt-4o-mini-2024-07-18",
    "system_fingerprint": "fp_efad92c60b",
    "choices": [
      {
        "index": 0,
        "message": {
          "role": "assistant",
          "content": ""
        },
        "finish_reason": "content_filter"
      }
    ],
    "usage": {
      "completion_tokens": 131,
      "prompt_tokens": 70,
      "total_tokens": 201
    }
  }
}
```

> ### Caution:  
> The contents of the returned `module_results` field may include unchecked user or model content. We recommend that you do not display this content to end users.

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

