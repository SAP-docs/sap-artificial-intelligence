<!-- loio7597e891128c405b97ea693e1690cfe2 -->

# Error Handling



If an error occurs, the response will contain an error code and message. The following examples show a request that is missing a parameter in the template:



### Example: V1

```
curl --request POST $ORCH_DEPLOYMENT_URL/completion \
    --header 'content-type: application/json' \
    --header "Authorization: Bearer $TOKEN" \
    --header "AI-Resource-Group: $RESOURCE_GROUP" \
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
          "model_name": "<ModelName>",
          "model_params": {
            "max_tokens": 300
          }
        }
      }
    },
    "input_params": {
      "number": "3"
    }
  }
```



### Example V2

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
              "name": "<model-name>",
              "params": {
                "max_completion_tokens": 300
               }
            }
          }
        }
      },
      "placeholder_values": { } // no placeholder_values supplied
    }
```



In this case, the response from the orchestration service contains an error code in the `code` field, a `message`, and a `location` indicating which orchestration module encountered the error.





### Output: V1

> ### Output Code:  
> ```
> {
>   "request_id": "3e988846-1360-4a4a-a7ad-e77b85057321",
>   "code": 400,
>   "message": "Missing required parameters: ['phrase']",
>   "location": "Module: Templating",
>   "module_results": {}
> }
> ```



### Output: V2

> ### Output Code:  
> ```
> {
>   "error": {
>     "request_id": "3e988846-1360-4a4a-a7ad-e77b85057321",
>     "code": 400,
>     "message": "400 - Input Parameters: Error validating parameters. Unused parameters: ['number', 'phrase'].",
>     "location": "Input Parameters",
>     "intermediate_results": {
>       "templating": [
>         {
>           "content": "Create {{?number}} paraphrases of {{?phrase}}",
>           "role": "user"
>         }
>       ]
>     }
>   }
> }
> ```

