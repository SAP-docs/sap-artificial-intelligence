<!-- loio2392d9a0504e4380bfa75a5efdb64b6e -->

# Consume Models with the Harmonized API

In this section, we will provide a minimal inference call without any orchestration modules.

A minimal call to orchestration contains only configurations of the required templating and model configuration modules. The curl command below shows how to make such a request.

> ### Sample Code:  
> ```
> curl --request POST $ORCH_DEPLOYMENT_URL/v2/completion \
> --header 'content-type: application/json' \
> --header "Authorization: Bearer $TOKEN" \
> --header "AI-Resource-Group: $RESOURCE_GROUP" \
> --data-raw '{
>   "config": {
>    "modules": {
>      "prompt_templating": {
>        "prompt": {
>          "template": [
>            {
>              "role": "user",
>              "content": "Reply with `{{?text}}` in {{?language}}"
>            }
>          ],
>          "defaults": {
>            "language": "English"
>          }
>        },
>        "model": {
>          "name": "<model>",
>          "params": {
>            "max_completion_tokens": 50,
>            "temperature": 0.1,
>            "frequency_penalty": 0,
>            "presence_penalty": 0
>          }
>        }
>      }
>    }
>   },
>   "placeholder_values": {
>    "text": "Orchestration is Working!",
>    "language": "German"
>   }
> }'
> ```

This request configures the templating module with a single user message with two parameters: `text` and `language`. The `language` parameter is also configured with English as the default. The LLM module is configured to use gpt-4o-mini in the latest available version and a set of model parameters. The `input_params` field contains the values for the parameters `text` and `language`. These values are used during this request in the prompt sent to the model.

The response contains a `request_id`, the module results from each module that was executed, and the `orchestration_result`, which includes the response of the call to the model. For more information about modules available for consumption using the Harmoized API, see [Orchestration](orchestration-8d02235.md).

> ### Output Code:  
> ```
> {
>   "request_id": "d8efd339-8ae1-9810-a076-22360875a2fe",
>   "intermediate_results": {
>     "templating": [
>       {
>         "content": "Reply with `Orchestration is Working!` in German",
>         "role": "user"
>       }
>     ],
>     "llm": {
>       "id": "chatcmpl-D2VKMLhpxnszJKVXeNP0k6OcJTQDK",
>       "object": "chat.completion",
>       "created": 1769489450,
>       "model": "gpt-4o-2024-08-06",
>       "system_fingerprint": "fp_4a331a0222",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "Die Orchestrierung funktioniert!"
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 7,
>         "prompt_tokens": 19,
>         "total_tokens": 26,
>         "prompt_tokens_details": {
>           "audio_tokens": 0,
>           "cached_tokens": 0
>         },
>         "completion_tokens_details": {
>           "accepted_prediction_tokens": 0,
>           "audio_tokens": 0,
>           "reasoning_tokens": 0,
>           "rejected_prediction_tokens": 0
>         }
>       }
>     }
>   },
>   "final_result": {
>     "id": "chatcmpl-D2VKMLhpxnszJKVXeNP0k6OcJTQDK",
>     "object": "chat.completion",
>     "created": 1769489450,
>     "model": "<model><modelversion>",
>     "system_fingerprint": "fp_4a331a0222",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "Die Orchestrierung funktioniert!"
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 7,
>       "prompt_tokens": 19,
>       "total_tokens": 26,
>       "prompt_tokens_details": {
>         "audio_tokens": 0,
>         "cached_tokens": 0
>       },
>       "completion_tokens_details": {
>         "accepted_prediction_tokens": 0,
>         "audio_tokens": 0,
>         "reasoning_tokens": 0,
>         "rejected_prediction_tokens": 0
>       }
>     }
>   }
> }
> ```

The templating module result contains the user message with the filled in parameters. The LLM module result contains the response of the model execution. In this example, the LLM module result and the orchestration result are the same. However, they might differ, such as when the output filtering module filters the response.

**Related Information**  


[Consumption of GenAI Models Using Orchestration – A Beginner's Guide](https://developers.sap.com/tutorials/ai-core-orchestration-consumption.html)

[Libraries and SDKs](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/499309d6e371419fb7a88b7d68c20a31.html "Explore additional SDKs and libraries that you can use with SAP AI Core.") :arrow_upper_right:

