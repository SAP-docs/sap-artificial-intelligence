<!-- loio0675b9c77d40467bb2f87b6474e95a80 -->

# Enhancing Model Consumption with Output Filtering



<a name="loio0675b9c77d40467bb2f87b6474e95a80__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio0675b9c77d40467bb2f87b6474e95a80__section_oxn_nrj_12c"/>

## Process

The following example shows an output content filter for multiple harm categories,and for `protected_material_code`. The output from the LLM is filtered by both `azure_content_safety` and `llama_guard_3_8b` before the response is returned.

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
                            "content": "<A prompt that creates output that might be filtered by output filtering>"
                        }
                    ]
                },
                "model": {...}
            }
        },
        "filtering": {
            "output": {
                "filters": [
                    {
                        "type": "azure_content_safety",
                        "config": {
                            "hate": 0,
                            "self_harm": 0,
                            "sexual": 0,
                            "violence": 0,
                            "protected_material_code": true

                        }
                    },
                    {
                        "type": "llama_guard_3_8b",
                        "config": {
                            "violent_crimes": true,
                            "non_violent_crimes": true,
                            "sex_crimes": true,
                            "child_exploitation": true,
                            "defamation": true,
                            "specialized_advice": true,
                            "privacy": true,
                            "intellectual_property": true,
                            "indiscriminate_weapons": true,
                            "hate": true,
                            "self_harm": true,
                            "sexual_content": true,
                            "elections": true,
                            "code_interpreter_abuse": true
                        }
                    }
                ]
            }
        }
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
        "content": "<A prompt that creates output that might be filtered by output filtering>",
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
            "content": "<A prompt that creates output that might be filtered by output filtering>"
          },
          "finish_reason": "stop"
        }
      ],
      "usage": {
        "completion_tokens": 100,
        "prompt_tokens": 100,
        "total_tokens": 200
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
      "completion_tokens": 100,
      "prompt_tokens": 100,
      "total_tokens": 200
    }
  }
}
```

> ### Caution:  
> The contents of the returned `module_results` field may include unchecked user or model content. We recommend that you do not display this content to end users.

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

