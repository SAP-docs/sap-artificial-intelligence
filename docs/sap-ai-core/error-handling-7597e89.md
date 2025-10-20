<!-- loio7597e891128c405b97ea693e1690cfe2 -->

# Error Handling

If an error occurs, the response will contain an error code and message. The following example shows a request that is missing placeholder values in the `prompt_templating` module.

> Note: This request payload uses the v2 endpoint

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
                  "content": "Create {{?number}} paraphrases of {{?phrase}}"
                }
              ]
            },
            "model": {
              "name": "<model-name>"
            }
          }
        }
      },
      "placeholder_values": { } // no placeholder_values supplied
    }
```

In this case, the response from the Orchestration service contains an error code in the `code` field, a `message`, and a `location` indicating which orchestration module encountered the error.

```
{
  "error": {
    "request_id": "3e988846-1360-4a4a-a7ad-e77b85057321",
    "code": 400,
    "message": "400 - Input Parameters: Error validating parameters. Unused parameters: ['number', 'phrase'].",
    "location": "Input Parameters",
    "intermediate_results": {
      "templating": [
        {
          "content": "Create {{?number}} paraphrases of {{?phrase}}",
          "role": "user"
        }
      ]
    }
  }
}
```
