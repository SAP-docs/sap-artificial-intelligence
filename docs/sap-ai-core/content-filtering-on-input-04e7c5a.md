<!-- loio04e7c5ad19f44a5ea2b4ebc4dd06fda9 -->

# Content Filtering on Input

The content filter is configured using the `filtering_module_config` field of the `module_configurations`. You can configure different scores for each of the four content categories \(that is, `Hate`, `Violence`, `Sexual`, and `SelfHarm`\). Lower scores for these categories mean that filtering is stricter – everything classified with a severity above the configured thresholds will be filtered. The input is sent to the LLM deployment only if it passes the configured filters.

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

