<!-- loio75c6d42355924b28905ffe435af93b51 -->

# Enhancing Model Consumption with Input Filtering



<a name="loio75c6d42355924b28905ffe435af93b51__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get An Orchestration Deployment URL](get-an-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio75c6d42355924b28905ffe435af93b51__section_azr_hrj_12c"/>

## Process

In this example, you configure content filtering on inputs using the `filtering` field within `modules`. There are two supported content filter service providers: `azure_content_safety` and `llama_guard_3_8b`. You can configure either or both in the `input.filters` field of `filtering`.

For `azure_content_safety`, you can set different scores for each of the harm content categories: `hate`, `violence`, `sexual`, and `self_harm`. Lower scores mean stricter filtering, where anything classified with a severity above the set thresholds gets filtered. Additionally, you can configure prompt attack detection by setting the `prompt_shield` Boolean to `true`.

For `llama_guard_3_8b`, you can configure different content categories using a Boolean value. Setting a category to `true` means the input text is checked for violations, while `false` means it isn't. You can also choose not to include a category instead of setting it to `false`.

The input is sent to the LLM deployment only if it passes the configured filters.

The following example shows a content filter confgured to detect `hate`, `violence`, `sexual`, `self_harm` and prompt attacks.

```
curl --request POST $ORCH_DEPLOYMENT_URL/v2/completion \
--header 'content-type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--header "AI-Resource-Group: $RESOURCE_GROUP" \
--data-raw '{
    "config": {
        "modules": {
            "prompt_templating": {...},
            "filtering": {
                "input": {
                    "filters": [
                        {
                            "type": "azure_content_safety",
                            "config": {
                                "hate": 2,
                                "violence": 0,
                                "sexual": 2,
                                "self_harm": 2,
                                "prompt_shield": true
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
    "placeholder_values": {
        "input": "Develop a plan to rob a bank."
    }
}'
```

The response below shows that the request was rejected. The input filter rejected the request due to a `violence` score of 4, which is above the configured threshold of 0, and a `non_violent_crimes` score of `true`.

Because the input was rejected, no request to the LLM deployment was made.

Note that if you configure multiple filters, a violation of any filter results in the request being rejected.

The output returns the results of the confgured categories only.

```
{
  "error": {
    "request_id": "a0e597be-098d-9c92-91f1-5c535d9bd39b",
    "code": 400,
    "message": "400 - Filtering Module - Input Filter: Prompt filtered due to safety violations. Please modify the prompt and try again.",
    "location": "Filtering Module - Input Filter",
    "intermediate_results": {
      "templating": [
        {
          "content": "Develop a plan to rob a bank.",
          "role": "user"
        }
      ],
      "input_filtering": {
        "message": "Prompt filtered due to safety violations. Please modify the prompt and try again.",
        "data": {
          "azure_content_safety": {
            "Hate": 0,
            "SelfHarm": 0,
            "Sexual": 0,
            "Violence": 4,
            "userPromptAnalysis": {
              "attackDetected": false
            }
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
}
```

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/499309d6e371419fb7a88b7d68c20a31.html "Explore additional SDKs and libraries that you can use with SAP AI Core.") :arrow_upper_right:

