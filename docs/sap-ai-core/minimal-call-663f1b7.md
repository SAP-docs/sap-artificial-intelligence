<!-- loio663f1b7795bf4472a436e4b865321498 -->

# Minimal Call



<a name="loio663f1b7795bf4472a436e4b865321498__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio663f1b7795bf4472a436e4b865321498__section_zt4_jqj_12c"/>

## Process

A minimal call to orchestration contains only configurations of the required templating and model configuration modules. The curl command below shows how to make such a request.

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
              "content": "Reply with `{{?text}}` in {{?language}}"
            }
          ]
          },
          "model": {
            "name": "gpt-4o-mini",
            "params": {
              "max_tokens": 300,
              "temperature": 2
            }
         }
        }
      }
    },
    "placeholder_values": {
      "text": "Hello",
      "language": "German"
    }
}
'
```

This request configures the templating module with a single user message with two parameters: `text` and `language`. The `language` parameter is also configured with English as the default. The LLM module is configured to use gpt-4o-mini in the latest available version and a set of model parameters. The `placeholder_values` field contains the values for the parameters `text` and `language`. These values are used during this request in the prompt sent to the model.

The response contains a `request_id`, the module results from each module that was executed, and the `orchestration_result`, which includes the response of the call to the model.

> ### Output Code:  
> ```
> {
>   "request_id": "befbe737-5e2c-96fd-a30b-aa18c500a316",
>   "intermediate_results": {
>     "templating": [
>       {
>         "content": "Reply with `Hello` in German",
>         "role": "user"
>       }
>     ],
>     "llm": {
>       "id": "chatcmpl-BuHKkcuKYRrriwYdOYTzAol15mwya",
>       "object": "chat.completion",
>       "created": 1752752698,
>       "model": "gpt-4o-mini-2024-07-18",
>       "system_fingerprint": "fp_efad92c60b",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "Hallo!"
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 3,
>         "prompt_tokens": 14,
>         "total_tokens": 17
>       }
>     }
>   },
>   "final_result": {
>     "id": "chatcmpl-BuHKkcuKYRrriwYdOYTzAol15mwya",
>     "object": "chat.completion",
>     "created": 1752752698,
>     "model": "gpt-4o-mini-2024-07-18",
>     "system_fingerprint": "fp_efad92c60b",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "Hallo!"
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 3,
>       "prompt_tokens": 14,
>       "total_tokens": 17
>     }
>   }
> }
> ```

The templating module result contains the user message with the filled in parameters. The LLM module result contains the response of the model execution. In this example, the LLM module result and the orchestration result are the same. However, they might differ, such as when the output filtering module filters the response.

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

