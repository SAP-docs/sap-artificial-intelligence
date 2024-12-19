<!-- loio4fe47b13f9864878aed50bf9d4ef00e1 -->

# Few-Shot Learning

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

