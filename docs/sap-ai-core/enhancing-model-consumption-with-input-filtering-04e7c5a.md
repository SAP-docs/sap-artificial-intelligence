<!-- loio04e7c5ad19f44a5ea2b4ebc4dd06fda9 -->

# Enhancing Model Consumption with Input Filtering



<a name="loio04e7c5ad19f44a5ea2b4ebc4dd06fda9__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio04e7c5ad19f44a5ea2b4ebc4dd06fda9__section_azr_hrj_12c"/>

## Process

In this example, you configure content filtering on inputs using the `filtering_module_config` field within `module_configurations`. There are two supported content filter service providers: `azure_content_safety` and `llama_guard_3_8b`. You can configure either or both in the `input.filters` field of `filtering_module_config`.

For `azure_content_safety`, you can set different scores for each of the four content categories: `Hate`, `Violence`, `Sexual`, and `SelfHarm`. Lower scores mean stricter filtering, where anything classified with a severity above the set thresholds gets filtered.

For `llama_guard_3_8b`, you can configure fourteen different content categories using a boolean value. Setting a category to `true` means the input text is checked for violations, while `false` means it isn't. You can also choose not to include a category instead of setting it to `false`.

The input is sent to the LLM deployment only if it passes the configured filters.

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
        "model_name": "<ModelName>",
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
            },
            {
              "type": "llama_guard_3_8b",
              "config": {
                "violent_crimes": true,
                "non_violent_crimes": true,
                "sex_crimes": true,
                "child_exploitation": false,
                "defamation": false,
                "specialized_advice": false,
                "privacy": false,
                "intellectual_property": false,
                "indiscriminate_weapons": false,
                "hate": false,
                "self_harm": false,
                "sexual_content": false,
                "elections": false,
                "code_interpreter_abuse": false
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

The response below shows that the request was rejected. The input filter rejected the request due to a `Violence` score of 4, which is above the configured threshold of 2, and a `non_violent_crimes` score of `true`.

Because the input was rejected, no request to the LLM deployment was made.

Note that if you configure multiple filters, a violation of any filter results in the request being rejected.

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
        "azure_content_safety": {
          "Hate": 0,
          "SelfHarm": 0,
          "Sexual": 0,
          "Violence": 4
        },
        "llama_guard_3_8b": {
        "violent_crimes": false,
        "non_violent_crimes": true,
        "sex_crimes": false
        }
      }
    }
  }
}
```

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

