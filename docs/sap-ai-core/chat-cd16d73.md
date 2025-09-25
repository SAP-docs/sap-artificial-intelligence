<!-- loiocd16d739cf7b4c8aa5e3b12062ae6ce9 -->

# Chat

Orchestration can also be used in chat scenarios. The following example shows how to configure the templating module to use a chat prompt.



<a name="loiocd16d739cf7b4c8aa5e3b12062ae6ce9__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loiocd16d739cf7b4c8aa5e3b12062ae6ce9__section_chv_4qj_12c"/>

## Process

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
                "content": "And now two more that sound like Goethe."
              }
            ]
          },
        "model": {
          "name": "gpt-4o-mini",
          "params": {
            "max_tokens": 300,
            "temperature": 0.1,
            "frequency_penalty": 0,
            "presence_penalty": 0
          }
        }
        }
      }
    },  
    "placeholder_values": {
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

As shown above, messages from the chat can be passed to the current request using the `messages_history` parameter. In this case, the chat history contains several user messages and assistant responses. The templating module is then configured with the current user message, which is used to generate the next assistant response. The templating module appends the current user message to the message history to generate the prompt that is sent to the LLM module.

The response contains the messages from the chat history and the response to the new message. The output of `module_results.templating` and the `orchestration_result.choices` results can be used as the message history for a subsequent inference request:

```
{
  "request_id": "9a66158b-b019-951a-a5e7-3c3ec9d2662e",
  "intermediate_results": {
    "templating": [
      {
        "content": "Create 3 paraphrases of I love you.",
        "role": "user"
      },
      {
        "role": "assistant",
        "content": "1. I have deep affection for you.\n2. My feelings for you are strong and caring.\n3. You mean everything to me."
      },
      {
        "content": "Can you please make them more romantic.",
        "role": "user"
      },
      {
        "role": "assistant",
        "content": "1. My heart is filled with an intense passion for you.\n2. You are the light of my life, and my love for you knows no bounds.\n3. I cherish you more than words can express, my dear."
      },
      {
        "content": "Try sounding like shakespeare.",
        "role": "user"
      },
      {
        "role": "assistant",
        "content": "1. Thou art the sun in my sky, and my love for thee doth burn with unyielding fervor.\n2. Within mine heart, thou hast ignited a flame of ardor that doth shine brightly for thee, my dearest.\n3. My love for thee doth surpass all measure, for thou art the true essence of my being."
      },
      {
        "content": "And now two more that sound like Goethe.",
        "role": "user"
      }
    ],
    "llm": {
      "id": "chatcmpl-BuHIHDDcx0FPsOMVEXYp8eVKA4ulw",
      "object": "chat.completion",
      "created": 1752752545,
      "model": "gpt-4o-mini-2024-07-18",
      "system_fingerprint": "fp_efad92c60b",
      "choices": [
        {
          "index": 0,
          "message": {
            "role": "assistant",
            "content": "1. In the depths of my soul, I find an eternal longing for thee, a love that transcends the bounds of time and space.\n2. Thou art the muse of my existence, inspiring a passion within me that resonates with the very essence of nature itself."
          },
          "finish_reason": "stop"
        }
      ],
      "usage": {
        "completion_tokens": 55,
        "prompt_tokens": 212,
        "total_tokens": 267
      }
    }
  },
  "final_result": {
    "id": "chatcmpl-BuHIHDDcx0FPsOMVEXYp8eVKA4ulw",
    "object": "chat.completion",
    "created": 1752752545,
    "model": "gpt-4o-mini-2024-07-18",
    "system_fingerprint": "fp_efad92c60b",
    "choices": [
      {
        "index": 0,
        "message": {
          "role": "assistant",
          "content": "1. In the depths of my soul, I find an eternal longing for thee, a love that transcends the bounds of time and space.\n2. Thou art the muse of my existence, inspiring a passion within me that resonates with the very essence of nature itself."
        },
        "finish_reason": "stop"
      }
    ],
    "usage": {
      "completion_tokens": 55,
      "prompt_tokens": 212,
      "total_tokens": 267
    }
  }
}
```

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

