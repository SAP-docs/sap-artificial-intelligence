<!-- loio949e7737f8fc4d88a02dc13a6e261d76 -->

# Minimal Call

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

This request configures the templating module with a single user message with two parameters: `text` and `language`. The `language` parameter is also configured with English as the default. The LLM module is configured to use gpt-35-turbo-16k in the latest available version and a set of model parameters. The `input_params` field contains the values for the parameters `text` and `language`. These values are used during this request in the prompt sent to the model.

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

The templating module result contains the user message with the filled in parameters. The LLM module result contains the response of the model execution. In this example, the LLM module result and the orchestration result are the same. However, they might differ, such as when the output filtering module filters the response.

