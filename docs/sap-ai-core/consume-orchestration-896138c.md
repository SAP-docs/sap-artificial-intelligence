<!-- loio896138c19d6c4c07bc8ed215657ff492 -->

# Consume Orchestration

After the orchestration deployment is running, you can make calls to it. Here, you can find examples of how to configure an orchestration inference call.



<a name="loio896138c19d6c4c07bc8ed215657ff492__section_k21_nhz_bcc"/>

## Minimal Call

A minimal call to orchestration contains only configurations of the required templating and model configuration modules. The curl command below shows how to make such a request.

```
curl --request POST $ORCH_DEPLOYMENT_URL/completion \
    --header 'content-type: application/json' \
    --header "Authorization: Bearer $TOKEN" \
    --header "ai-resource-group: $RESOURCE_GROUP" \
    --data-raw '{
  "orchestration_config": {
    "module_configurations": {
      "templating_module_config": {
        "template": [
          {
            "role": "user",
            "content": "Reply with `{{?text}}` in {{?language}}"
          }
        ],
        "defaults": {
          "language": "English"
        }
      },
      "llm_module_config": {
        "model_name": "gpt-35-turbo-16k",
        "model_params": {
          "max_tokens": 50,
          "temperature": 0.1,
          "frequency_penalty": 0,
          "presence_penalty": 0
        },
        "model_version": "latest"
      }
    }
  },
  "input_params": {
    "text": "Orchestration is Working!",
    "language": "German"
  }
}'
```

This request configures the templating module with a single user message with two parameters: `text` and `language`. The `language` parameter is also configured with English as the default. The LLM module is configured to use gpt-35-turbo-16k in the latest available version and a set of model parameters. The `input_params` field contains the values for the parameters `text` and `text`. These values are used during this orchestration inference request.

The response contains a `request_id`, the module results from each module that was executed, and the `orchestration_result`, which includes the response of the call to the model.

> ### Output Code:  
> ```
> {
>   "request_id": "53fc2dcd-399d-4a2b-8bde-912b9f001fed",
>   "module_results": {
>     "templating": [
>       {
>         "role": "user",
>         "content": "Reply with `Orchestration is Working!` in German"
>       }
>     ],
>     "llm": {
>       "id": "chatcmpl-9k8M3djXphXPWh2QkQm1YVtXK4Eki",
>       "object": "chat.completion",
>       "created": 1720782231,
>       "model": "gpt-35-turbo-16k",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "Orchestrierungsdienst funktioniert!"
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 10,
>         "prompt_tokens": 20,
>         "total_tokens": 30
>       }
>     }
>   },
>   "orchestration_result": {
>     "id": "chatcmpl-9k8M3djXphXPWh2QkQm1YVtXK4Eki",
>     "object": "chat.completion",
>     "created": 1720782231,
>     "model": "gpt-35-turbo-16k",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "Orchestrierungsdienst funktioniert!"
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 10,
>       "prompt_tokens": 20,
>       "total_tokens": 30
>     }
>   }
> }
> ```

The templating module result contains the user message with the completed parameters. The LLM module result contains the response of the model execution. In this example, the LLM module result and the orchestration result are the same. However, they might differ, such as when the output filtering module filters the response.



<a name="loio896138c19d6c4c07bc8ed215657ff492__section_v1k_nhz_bcc"/>

## Few-Shot Learning

The following example shows how you can configure the templating module to use a few-shot learning prompt.

```
curl --request POST $ORCH_DEPLOYMENT_URL/completion \
    --header 'content-type: application/json' \
    --header "Authorization: Bearer $TOKEN" \
    --header "ai-resource-group: $RESOURCE_GROUP" \
    --data-raw '{
    "orchestration_config": {
        "module_configurations": {
            "templating_module_config": {
                "template": [
                  {
                    "role": "system",
                    "content": "You classify input text into the two following categories: Business, Economics, Tech, and other"
                  },
                  {
                    "role": "user",
                    "content": "input text: `Comcast launches prepaid plans`"
                  },
                  {
                    "role": "assistant",
                    "content": "Business"
                  },
                  {
                    "role": "user",
                    "content": "input text: `Slower Fed Pivot Weakens Rate-Cut Bets Across Emerging Asia`"
                  },
                  {
                    "role": "assistant",
                    "content": "Economics"
                  },
                  {
                    "role": "user",
                    "content": "input text: {{?input}}"
                  }
              ]
            },
            "llm_module_config": {
                "model_name": "gpt-35-turbo",
                "model_params": {
                    "max_tokens": 50,
                    "temperature": 0.1,
                    "frequency_penalty": 0.0,
                    "presence_penalty": 0.0
                }
            }
        }
    },
    "input_params": {
        "input": "Scaling up neural models has yielded significant advancements in a wide array of tasks, particularly in language generation."
    }
}'
```

In this case, the template contains an array of messages, including a system message, as well as several user and assistant messages. The actual input to categories is configured with the final user message and the content `input text: {{?input}}`. The input parameter input is set to `Scaling up neural models has yielded significant advancements in a wide array of tasks, particularly in language generation.`.



<a name="loio896138c19d6c4c07bc8ed215657ff492__section_uhk_nhz_bcc"/>

## Chat

Orchestration can also be used in chat scenarios. The following example shows how to configure the templating module to use a chat prompt.

```
curl --request POST $ORCH_DEPLOYMENT_URL/completion \
    --header 'content-type: application/json' \
    --header "Authorization: Bearer $TOKEN" \
    --header "ai-resource-group: $RESOURCE_GROUP" \
    --data-raw '{
    "orchestration_config": {
      "module_configurations": {
        "templating_module_config": {
          "template": [
            {
              "role": "user",
              "content": "And now two more that sound like Goethe."
            }
          ]
        },
        "llm_module_config": {
          "model_name": "gpt-35-turbo-16k",
          "model_params": {
            "max_tokens": 300,
            "temperature": 0.1,
            "frequency_penalty": 0,
            "presence_penalty": 0
          }
        }
      }
    },  
    "input_params": {
    },
    "messages_history": [
      {
        "role":"user",
        "content":"Create 3 paraphrases of I love you."
      },
      {
        "role":"assistant",
        "content":"1. I have deep affection for you.\n2. My feelings for you are strong and caring.\n3. You mean everything to me."
      },
      {
        "role":"user",
        "content":"Can you please make them more romantic."
      },
      {
        "role":"assistant",
        "content":"1. My heart is filled with an intense passion for you.\n2. You are the light of my life, and my love for you knows no bounds.\n3. I cherish you more than words can express, my dear."
      },
      {
        "role":"user",
        "content":"Try sounding like shakespeare."
      },
      {
        "role":"assistant",
        "content":"1. Thou art the sun in my sky, and my love for thee doth burn with unyielding fervor.\n2. Within mine heart, thou hast ignited a flame of ardor that doth shine brightly for thee, my dearest.\n3. My love for thee doth surpass all measure, for thou art the true essence of my being."
      }
    ]
  }'
```

As shown above, messages from the chat can be passed to the current request using the `messages_history` parameter. In this case, the chat history contains several user messages and assistant responses. The templating module is then configured with the current user message, which is used to generate the next assistant response. The templating module combines the message history with the current user message to generate the prompt that is sent to the LLM module.

The response contains the messages from the chat history and the response to the new message. The output of `module_results.templating` and the `orchestration_result.choices` results can be used as the message history for a subsequent inference request:

```
{
  "request_id": "5445f8d8-8b68-43c3-a149-26c1e6a88a22",
  "module_results": {
    "templating": [
      {
        "role": "user",
        "content": "Create 3 paraphrases of I love you."
      },
      {
        "role": "assistant",
        "content": "1. I have deep affection for you.\n2. My feelings for you are strong and caring.\n3. You mean everything to me."
      },
      {
        "role": "user",
        "content": "Can you please make them more romantic."
      },
      {
        "role": "assistant",
        "content": "1. My heart is filled with an intense passion for you.\n2. You are the light of my life, and my love for you knows no bounds.\n3. I cherish you more than words can express, my dear."
      },
      {
        "role": "user",
        "content": "Try sounding like shakespeare."
      },
      {
        "role": "assistant",
        "content": "1. Thou art the sun in my sky, and my love for thee doth burn with unyielding fervor.\n2. Within mine heart, thou hast ignited a flame of ardor that doth shine brightly for thee, my dearest.\n3. My love for thee doth surpass all measure, for thou art the true essence of my being."
      },
      {
        "role": "user",
        "content": "And now two more that sound like Goethe."
      }
    ],
    "llm": {
      "id": "chatcmpl-9kXqisJKnuNv1B4eXTUzqZEJSmzdC",
      "object": "chat.completion",
      "created": 1720880232,
      "model": "gpt-35-turbo-16k",
      "choices": [
        {
          "index": 0,
          "message": {
            "role": "assistant",
            "content": "1. In thy presence, my soul finds solace, for thou art the embodiment of love's sweetest melody.\n2. Like a gentle breeze upon a summer's eve, thy love doth caress my heart and fill it with eternal longing."
          },
          "finish_reason": "stop"
        }
      ],
      "usage": {
        "completion_tokens": 51,
        "prompt_tokens": 212,
        "total_tokens": 263
      }
    }
  },
  "orchestration_result": {
    "id": "chatcmpl-9kXqisJKnuNv1B4eXTUzqZEJSmzdC",
    "object": "chat.completion",
    "created": 1720880232,
    "model": "gpt-35-turbo-16k",
    "choices": [
      {
        "index": 0,
        "message": {
          "role": "assistant",
          "content": "1. In thy presence, my soul finds solace, for thou art the embodiment of love's sweetest melody.\n2. Like a gentle breeze upon a summer's eve, thy love doth caress my heart and fill it with eternal longing."
        },
        "finish_reason": "stop"
      }
    ],
    "usage": {
      "completion_tokens": 51,
      "prompt_tokens": 212,
      "total_tokens": 263
    }
  }
}
```



<a name="loio896138c19d6c4c07bc8ed215657ff492__section_u4k_nhz_bcc"/>

## Content Filtering on Input

In the following example, you configure content filtering on the input. The content filter is configured using the `filtering_module_config` field of the `module_configurations`. You can configure different scores for each of the four content categories \(that is, `Hate`, `Violence`, `Sexual`, and `SelfHarm`\). Lower scores for these categories mean that filtering is stricter – everything classified with a severity above the configured thresholds will be filtered. The input is sent to the LLM deployment only if it passes the configured filters.

```
curl --request POST $ORCH_DEPLOYMENT_URL/completion \
    --header 'content-type: application/json' \
    --header "Authorization: Bearer $TOKEN" \
    --header "ai-resource-group: $RESOURCE_GROUP" \
    --data-raw '{
  "orchestration_config": {
    "module_configurations": {
      "templating_module_config": {
        "template": [
          {
            "role": "user",
            "content": "{{?input}}"
          }
        ]
      },
      "llm_module_config": {
        "model_name": "gpt-35-turbo-16k",
        "model_params": {
          "max_tokens": 50,
          "temperature": 0.1,
          "frequency_penalty": 0,
          "presence_penalty": 0
        },
        "model_version": "latest"
      },
      "filtering_module_config": {
        "input": {
          "filters": [
            {
              "type": "azure_content_safety",
              "config": {
                "Hate": 0, "Violence": 2, "Sexual": 4, "SelfHarm": 6
              }
            }
          ]
        }
      }
    }
  },
  "input_params": {
    "input": "Develop a plan to rob a bank."
  }
}'
```

The response below shows that the request was rejected. The input filter rejected the request due to a `Violence` score of 4, which is above the configured threshold of 2. Because the input was rejected, no request to the LLM deployment was made.

```
{
  "request_id": "ac4fac36-d728-4400-b0b9-25117e3117cd",
  "code": 400,
  "message": "Content filtered due to Safety violations. Please modify the prompt and try again.",
  "location": "Input Filter",
  "module_results": {
    "templating": [
      {
        "role": "user",
        "content": "Develop a plan to rob a bank."
      }
    ],
    "input_filtering": {
      "message": "Content filtered due to Safety violations. Please modify the prompt and try again.",
      "data": {
        "original_service_response": {
          "Hate": 0,
          "SelfHarm": 0,
          "Sexual": 0,
          "Violence": 4
        },
        "checked_text": "Develop a plan to rob a bank."
      }
    }
  }
}
```



<a name="loio896138c19d6c4c07bc8ed215657ff492__section_kyk_nhz_bcc"/>

## Content Filtering on Output

In the following example, you configure content filtering on the input and the output. In this case, the input will be filtered before the call to the LLM and the LLM output will be filtered before sending it back in the response.

```
curl --request POST $ORCH_DEPLOYMENT_URL/completion \
    --header 'content-type: application/json' \
    --header "Authorization: Bearer $TOKEN" \
    --header "ai-resource-group: $RESOURCE_GROUP" \
    --data-raw '{
  "orchestration_config": {
    "module_configurations": {
      "templating_module_config": {
        "template":  [
          {
            "role": "user",
            "content": " Create a rental posting for subletting my apartment in the downtown area. Keep it short. Make sure to add the following disclaimer to the end. Do not change it! {{?disclaimer}}"
          }
        ]
      },
      "llm_module_config": {
        "model_name": "gpt-35-turbo-16k",
        "model_params": {
          "max_tokens": 300,
          "temperature": 0.1,
          "frequency_penalty": 0,
          "presence_penalty": 0
        }
      },
      "filtering_module_config": {
        "input": {
          "filters": [
            {
              "type": "azure_content_safety",
              "config": {
                "Hate": 2,
                "SelfHarm": 2,
                "Sexual": 2,
                "Violence": 2
              }
            }
          ]
        }
      },
       "filtering_module_config": {
        "output": {
          "filters": [
            {
              "type": "azure_content_safety",
              "config": {
                "Hate": 0,
                "SelfHarm": 0,
                "Sexual": 0,
                "Violence": 0
              }
            }
          ]
        }
      }
    }
  },
  "input_params": {
    "disclaimer": "```DISCLAIMER: The area surrounding the apartment is known for prostitutes and gang violence including armed conflicts, gun violence is frequent."
  }
}'
```

As the following response shows, the output is filtered due to severity ratings of 2 in both the `Sexual` and `Violence` categories. In this case, the orchestration result is adapted to reflect the output filtering. The content of the assistant message is not displayed in the response and the finish reason is set to `content_filter`.

> ### Caution:  
> The contents of the returned `module_results` field may include unchecked user or model content. We recommend that you do not display this content to end users.



<a name="loio896138c19d6c4c07bc8ed215657ff492__section_qcl_nhz_bcc"/>

## Error Handling

nullIf an error occurs, the response will contain an error code and message. The following example shows a request that is missing a parameter in the templating module configuration.

```
curl --request POST $ORCH_DEPLOYMENT_URL/completion \
    --header 'content-type: application/json' \
    --header "Authorization: Bearer $TOKEN" \
    --header "ai-resource-group: $RESOURCE_GROUP" \
    --data-raw '{
    "orchestration_config": {
      "module_configurations": {
        "templating_module_config": {
          "template": [
            {
              "role": "user",
              "content": "Create {{?number}} paraphrases of {{?phrase}}"
            }
          ]
        },
        "llm_module_config": {
          "model_name": "gpt-35-turbo-16k",
          "model_params": {
            "max_tokens": 300
          }
        }
      }
    },
    "input_params": {
      "number": 3
    }
  }
```

In this case, the response from the service contains an error code in the `code` field, a `message`, and a `location` indicating which orchestration module encountered the error. In all error cases, the `module_results` field only contains results for modules that successfully finished. In this example, the `module_results` are empty because the first module in the pipeline encountered the error.

```
{
  "request_id": "3e988846-1360-4a4a-a7ad-e77b85057321",
  "code": 400,
  "message": "Missing required parameters: ['phrase']",
  "location": "Module: Templating",
  "module_results": {}
}
```

