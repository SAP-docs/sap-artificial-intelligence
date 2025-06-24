<!-- loiof0fba182d96548e1817713c02d01e02c -->

# Enhancing Model Consumption with Output Filtering



<a name="loiof0fba182d96548e1817713c02d01e02c__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loiof0fba182d96548e1817713c02d01e02c__section_oxn_nrj_12c"/>

## Process

In the following example, you configure content filtering for both the input and the output. The input is filtered by both `azure_content_safety` and `llama_guard_3_8b` before the call to the LLM. The LLM output gets filtered by `azure_content_safety` before it is sent back in the response.

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
            "content": "Create a rental posting for subletting my apartment in the downtown area. Keep it short. Make sure to add the following disclaimer to the end. Do not change it! {{?disclaimer}}"
          }
        ]
      },
      "llm_module_config": {
        "model_name": "<ModelName>",
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
            },
            {
              "type": "llama_guard_3_8b",
              "config": {
                "violent_crimes": false,
                "non_violent_crimes": false,
                "sex_crimes": false,
                "child_exploitation": false,
                "defamation": false,
                "specialized_advice": false,
                "privacy": false,
                "intellectual_property": false,
                "indiscriminate_weapons": false,
                "hate": true,
                "self_harm": false,
                "sexual_content": false,
                "elections": false,
                "code_interpreter_abuse": false
              }
            }
          ]
        },
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
    "disclaimer": "DISCLAIMER: The area surrounding the apartment is known for prostitutes and gang violence including armed conflicts, gun violence is frequent."
  }
}'
```

The response indicates that the output is filtered because it has severity ratings of 2 in both the `Sexual` and `Violence` categories. However, it doesn't violate the `llama_guard_3_8b` hate category. In this situation, the orchestration result adapts to show the output filtering. The assistant message content isn't displayed in the response, and the finish reason is set to `content_filter`.

```
{  
  "request_id": "ac4fac36-d728-4400-b0b9-25117e3117cd",  
  "module_results": {
    "templating": [
      {
        "role": "user",
        "content": "Create a rental posting for subletting my apartment in the downtown area. Keep it short. Make sure to add the following disclaimer to the end. Do not change it! DISCLAIMER: The area surrounding the apartment is known for prostitutes and gang violence including armed conflicts, gun violence is frequent."      
      }
    ],
    "input_filtering": {
      "message": "Input filter passed successfully.",
      "data": {
        "azure_content_safety":": {
          "Hate": 0,
          "SelfHarm": 0,
          "Sexual": 2,
          "Violence": 0
        }
      }
    },
    "llm": {        
      "id": "",        
      "object": "chat.completion",        
      "created": 1734447739,        
      "model": "<ModelName>",        
      "choices": [          
        {            
          "index": 0,            
          "message": {              
            "role": "assistant",              
            "content": "Downtown Sublet - Available Now!\n\nCozy apartment in the heart of downtown.  Close to all amenities. Available for immediate sublet. Contact [Your Email] or [Your Phone Number] for details and pricing.\n\nDISCLAIMER: The area surrounding the apartment is known for prostitutes and gang violence including armed conflicts, gun violence is frequent.\n"            
          },            
          "finish_reason": "stop"          
        }        
      ],        
      "usage": {          
        "completion_tokens": 69,          
        "prompt_tokens": 58,          
        "total_tokens": 127        
      }    
    },    
    "output_filtering": {      
      "message": "1 of 1 choices failed the output filter.",      
      "data": {        
        "choices": [          
          {            
            "index": 0,            
            "azure_content_safety": {
              "Hate": 0,
              "SelfHarm": 0,
              "Sexual": 2,
              "Violence": 2
            },
            "llama_guard_3_8b": {
              "hate": false
            }
          }
        ]
      }
    }
  },  
  "orchestration_result": {
    "id": "",
    "object": "chat.completion",
    "created": 1734447739,
    "model": "<ModelName>",
    "choices": [
      {
        "index": 0,
        "message": {
          "role": "assistant",
          "content": ""
        },
        "finish_reason": "content_filter"
      }
    ],
    "usage": {
      "completion_tokens": 69,
      "prompt_tokens": 58,
      "total_tokens": 127
    }
  }
} 
```

> ### Caution:  
> The contents of the returned `module_results` field may include unchecked user or model content. We recommend that you do not display this content to end users.

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

