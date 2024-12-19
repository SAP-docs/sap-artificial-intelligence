<!-- loiof0fba182d96548e1817713c02d01e02c -->

# Content Filtering on Output

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

