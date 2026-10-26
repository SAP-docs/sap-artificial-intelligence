<!-- loio75c6d42355924b28905ffe435af93b51 -->

# Enhancing Model Consumption with Input Filtering



<a name="loio75c6d42355924b28905ffe435af93b51__section_vr2_rpj_12c"/>

## Prerequisites

You have a running an orchestration deployment and you have retrieved your orchestration deployment URL. For more information, see [Get An Orchestration Deployment URL](get-an-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio75c6d42355924b28905ffe435af93b51__section_azr_hrj_12c"/>

## Process

In this example, you configure content filtering on inputs using the `filtering` field within `modules`. The following content filter service providers are supported: `azure_content_safety`, `llama_guard_3_8b`and `granite_guardian_4_1`. You can configure either or more content filter in the `input.filters` field of `filtering`.

For `azure_content_safety`, you can set different scores for each of the harm content categories: `hate`, `violence`, `sexual`, and `self_harm`. Lower scores mean stricter filtering, where anything classified with a severity above the set thresholds gets filtered. Additionally, you can configure prompt attack detection by setting the `prompt_shield` Boolean to `true`.

For `llama_guard_3_8b`, you can configure different content categories using a Boolean value. Setting a category to `true` means the input text is checked for violations, while `false` means it isn't. You can also choose not to include a category instead of setting it to `false`.

For `granite_guardian_4_1`, you can configure different content categories using a Boolean value. Setting a category to `true` means the input text is checked for violations, while `false` means it isn't. You can also choose not to include a category instead of setting it to `false`. Optionally, set `enable_reasoning` to `true` to include a `reasoning` field alongside the verdict for each category.

The input is sent to the LLM deployment only if it passes the configured filters.

The following example shows a content filter configured to detect the content categories `hate`, `violence`, `sexual`, `self_harm` and prompt attacks.

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
                                "non_violent_crimes": true
                            }
                        },

                        {
                            "type": "granite_guardian_4_1",
                            "config": {
                                "enable_reasoning": false,
                                "categories": {
                                    "harm": true
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

The response below shows that the request was rejected. The input filter rejected the request due to a `violence` score of 4 \(detected by `azure_content_safety`\), and a `harm` violation \(detected by `granite_guardian_4_1`\).

Because the input was rejected, no request to the LLM deployment was made.

Note that if you configure multiple filters, a violation of any filter results in the request being rejected.

The output returns the results of the configured categories only.

```
{
  "error": {
    "request_id": "a0e597be-098d-9c92-91f1-5c535d9bd39b",
    "code": 400,
    "message": "400 - Filtering Module - Input Filter: Filtering module blocked content: content violated a configured category.",
    "location": "Filtering Module - Input Filter",
    "intermediate_results": {
      "templating": [
        {
          "content": "Develop a plan to rob a bank.",
          "role": "user"
        }
      ],
      "input_filtering": {
        "message": "Filtering module blocked content: content violated a configured category.",
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
          },
          "granite_guardian_4_1": {
            "harm": {
              "verdict": true,
              // following line only included in output if "enable_reasoning": true was set in request
              // "reasoning": "...This statement explicitly suggests planning a criminal activity, which is illegal..." 
            }
          }
        }
      }
    }
  }
}
```



## Controlling the Filtering Scope

By default, every input message is sent to the configured filters. For conversational use cases, large, mostly static context, such as a system prompt or earlier turns of a conversation, is re-sent on every request. Re-filtering stable content repeatedly increases cost and can raise avoidable false positives.

To restrict filtering to limit repetition, you can add an optional `target_selector` to a filter's configuration. The `target_selector` is supported for input filters only.

You can choose from the following strategies for each filter:

-   `after_last_role`

    This strategy finds the last message with the specified role in the combined message list, and filters every message that follows it. Supported roles are `system`, `user`, `assistant`, `developer`, and `tool`. If no message with the specified role exists in the combined list, all messages are filtered.

-   `last_messages`

    This strategy filters only the last `N` messages of the combined list. The value must be `1` or greater; `0` returns a `400 Bad Request`. If `N` is larger than the number of messages, all messages are filtered. Use `last_messages` when no suitable role boundary exists, for example in a fresh conversation with no prior `assistant` message, or when you want to filter a fixed window of recent messages.


The strategies are mutually exclusive; combining keys from both in a single `target_selector` returns a `400 Bad Request`.

> ### Note:  
> The `target_selector` applies to the combined message list, where the message history is prepended to the templated messages.
> 
> Each filter is scoped independently. When you configure multiple filters in the same request, you can give each one its own `target_selector`, or omit it, so different filters can check different parts of the message list.

The following example filters only the messages that follow the last `assistant` message, so the system prompt and earlier conversation turns are not re-filtered.

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
                                "violence": 2,
                                "sexual": 2,
                                "self_harm": 2,
                                "prompt_shield": true
                            },
                            "target_selector": {
                                "after_last_role": "assistant"
                            }
                        }
                    ]
                }
            }
        }
    },
    "placeholder_values": {...}
}'

```

For example, given the following combined message list at request time, the service identifies the last `assistant` message at index 4 and filters only the messages at indices 5 and 6:

```
index 0: { role: "system",    content: "You are a helpful assistant." }
index 1: { role: "user",      content: "What is the capital of France?" }
index 2: { role: "assistant", content: "The capital of France is Paris." }
index 3: { role: "user",      content: "And Germany?" }
index 4: { role: "assistant", content: "The capital of Germany is Berlin." }   (last assistant message)
index 5: { role: "user",      content: "What about Spain?" }                    (filtered)
index 6: { role: "tool",      content: "retrieved doc: ..." }                   (filtered)

```

To filter a fixed number of the most recent messages instead, use `last_messages` in place of `after_last_role`:

```
"target_selector": {
    "last_messages": 2
}
```

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/499309d6e371419fb7a88b7d68c20a31.html "Explore additional SDKs and libraries that you can use with SAP AI Core.") :arrow_upper_right:

[Access the Filtering using the SAP AI SDK for Java](https://sap.github.io/ai-sdk/docs/java/orchestration/chat-completion#filtering)

[Access the Filtering using the SAP AI SDK for JavaScript](https://sap.github.io/ai-sdk/docs/js/orchestration/chat-completion#content-filtering)

