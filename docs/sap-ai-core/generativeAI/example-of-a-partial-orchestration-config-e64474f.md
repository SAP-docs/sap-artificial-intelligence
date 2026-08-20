<!-- loioe64474f3927744afbe2e2de1d12633c6 -->

# Example of a Partial Orchestration Config

Orchestration configs that lack mandatory fields \(such as model or prompt details\) can still be created, but the mandatory fields must be provided at time of consumption in Orchestration. In the following example, the prompt is missing:

```
curl -X POST "$AI_API_URL/v2/registry/v2/orchestrationConfigs" \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
    "name": "partial-orchestration-config",
    "version": "0.0.1",
    "scenario": "customer-support",
    "spec": {
      "modules": {
        "prompt_templating": {
          "model": {
            "name": "gpt-4o"
          }
        }
      }
    }
  }'
```

The following consumption example provides the mandatory prompt and an optional tool definition:

```
curl --request POST \
  --url $ORCHESTRATION_DEPLOYMENT_URL/v2/completion \
  --header "AI-Resource-Group: $RESOURCE_GROUP" \
  --header 'authorization: Bearer {{TOKEN}}' \
  --header 'content-type: application/json' \
  --data '{
  "config_ref": {
    "id": "b5ea5b32-0151-4608-98f6-d260dba6700d"
  },
  "config": {
    "modules": {
      "prompt_templating": {
        "prompt": {
          "template": [
            {
              "role": "user",
              "content": "What is the weather in Potsdam and in Toulouse in Celsius?"
            }
          ],
          "defaults": {},
          "tools": [
            {
              "type": "function",
              "function": {
                "description": "Get weather for location",
                "name": "getCurrentWeather",
                "parameters": {
                  "$schema": "https://json-schema.org/draft/2020-12/schema",
                  "additionalProperties": false,
                  "type": "object",
                  "properties": {
                    "arg0": {
                      "type": "object",
                      "properties": {
                        "location": {
                          "type": "string"
                        },
                        "unit": {
                          "type": "string",
                          "enum": [
                            "C",
                            "F"
                          ]
                        }
                      },
                      "required": [
                        "location",
                        "unit"
                      ]
                    }
                  },
                  "required": [
                    "arg0"
                  ]
                },
                "strict": false
              }
            }
          ]
        }
      }
    }
  }
}'
```

