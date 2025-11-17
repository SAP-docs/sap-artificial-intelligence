<!-- loio951d388a27004e15b8de9d026123fd3a -->

# Example Payloads for Inferencing - SAP AI Core Hosted

The following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).

> ### Tip:  
> If you use a Windows device, use Windows Powershell, and replace `curl` with `curl.exe`.

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $AUTH\_TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$DEPLOYMENT\_URL

</td>
<td valign="top">

The deployment URL for your generative AI model. For more information, see [Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-b32e7a8.md).

Alternatively, you can replace the `$DEPLOYMENT_URL` placeholder in the curl command with your deployment URL.

</td>
</tr>
</table>

For more information about supported parameters, see [Supported Parameters](supported-parameters-55d2197.md).



If you want to remove a model, delete its deployment. For more information, see [Delete a Single Deployment](delete-a-single-deployment-1b0b361.md) and [Delete Multiple Deployments](delete-multiple-deployments-6b521aa.md).

<a name="concept_vl1_fgm_pgc"/>

<!-- concept\_vl1\_fgm\_pgc -->

## Open Source

The `executableId` is `aicore-opensource`



<a name="concept_vl1_fgm_pgc__section_nmg_5rx_rcc"/>

## Meta Llama 3.1 70b instruct | Mistral Mixtral 8x7b instruct v01

For more information from the model providers, see [Meta Llama](https://huggingface.co/meta-llama/Llama-3.1-70B-Instruct) and [Mistral](https://huggingface.co/mistralai/Mixtral-8x7B-Instruct-v0.1).

Without streaming:

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "<ModelName>",
    "messages": [
        {
            "role": "user",
            "content": "Sample prompt"
        }
    ],
    "max_tokens": 100
}'
```

With streaming:

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "<ModelName>",
    "messages": [
        {
            "role": "user",
            "content": "Sample prompt"
        }
    ],
    "max_tokens": 100,
    "stream": true
}'
```

<a name="concept_jvv_fgm_pgc"/>

<!-- concept\_jvv\_fgm\_pgc -->

## Mistral

The `executableId` is `aicore-mistralai`

For more information from the model provider, see [Mistral Large](https://huggingface.co/mistralai/Mistral-Large-Instruct-2407) and [Mistral Small](https://huggingface.co/mistralai/Mistral-Small-3.1-24B-Instruct-2503).



<a name="concept_jvv_fgm_pgc__section_uz3_djx_4gc"/>

## mistralai--mistral-large-instruct | mistralai--mistral-small-instruct

**Text input**

Without streaming:

```

curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "<modelName>",
    "messages": [
        {
            "role": "user",
            "content": "Whats the difference between Accountability vs Responsibility, answer in 200 words?"
        }
    ],
    "max_tokens": 100
}'

```

> ### Output Code:  
> ```
> {
>     "choices": [
>         {
>             "finish_reason": "length",
>             "index": 0,
>             "logprobs": null,
>             "message": {
>                 "content": " Accountability and responsibility are related but distinct concepts.\n\n**Responsibility** is about the tasks and duties assigned to you. It's what you're expected to do as part of your role or agreement. For example, a project manager is responsible for planning and overseeing a project. Responsibility is often proactive and focuses on what you should do.\n\n**Accountability**, on the other hand, is about answering for the outcomes of your responsibilities. It",
>                 "role": "assistant",
>                 "tool_calls": []
>             },
>             "stop_reason": null
>         }
>     ],
>     "created": 1730096376,
>     "id": "<id>",
>     "model": "<modelName>",
>     "object": "chat.completion",
>     "usage": {
>         "completion_tokens": 100,
>         "prompt_tokens": 23,
>         "total_tokens": 123
>     }
> ```

With streaming:

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "<ModelName>",
    "messages": [
        {
            "role": "user",
            "content": "Sample prompt"
        }
    ],
    "max_tokens": 100,
    "stream": true
}'
```

**Image input** \(for mistralai--mistral-small-instruct only\):

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "<modelName>",
    "messages": [
        {
            "role": "user",
            "content": [
                {
                    "type": "image_url",
                    "image_url": {
                        "url": "https://url/pexels-field-1-1024×683.jpg"
                    }
                }
            ]
        }
    ],
    "max_tokens": 10
}'
```

> ### Output Code:  
> ```
> {
>   "choices": [
>     {
>       "finish_reason": "length",
>       "index": 0,
>       "logprobs": null,
>       "message": {
>         "content": "The image shows a picturesque countryside landscape, likely",
>         "reasoning_content": null,
>         "role": "assistant",
>         "tool_calls": []
>       },
>       "stop_reason": null
>     }
>   ],
>   "created": 1748573681,
>   "id": "<id>",
>   "model": "<modelName>",
>   "object": "chat.completion",
>   "prompt_logprobs": null,
>   "usage": {
>     "completion_tokens": 10,
>     "prompt_tokens": 953,
>     "prompt_tokens_details": null,
>     "total_tokens": 963
>   }
> }
> ```

> ### Note:  
> For information on metering of image input, see[Images](metering-and-pricing-for-generative-ai-41e8d85.md#loio41e8d85586f64e7184f388f8d58624a8__section_w4y_hpl_nfc).



## mistralai--mistral-medium-instruct

For more information from the model provider, see [Mistral Models](https://docs.mistral.ai/getting-started/models/models_overview/).



### Text Generation

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "mistralai--mistral-medium-instruct",
    "messages": [
            {
              "role": "user", 
              "content": "Give me a JSON object with a person's name and age."
            }
    ],
    "response_format": { 
      "type": "json_object"
    }
}'
```

> ### Output Code:  
> ```
> {
>   "id": "<id>",
>   "object": "chat.completion",
>   "created": 1757916217,
>   "model": "mistralai--mistral-medium-instruct",
>   "choices": [
>     {
>       "index": 0,
>       "message": {
>         "role": "assistant",
>         "reasoning_content": null,
>         "content": "{\"name\": \"John Doe\", \"age\": 30}",
>         "tool_calls": []
>       },
>       "logprobs": null,
>       "finish_reason": "stop",
>       "stop_reason": null
>     }
>   ],
>   "usage": {
>     "prompt_tokens": 16,
>     "total_tokens": 31,
>     "completion_tokens": 15,
>     "prompt_tokens_details": null
>   },
>   "prompt_logprobs": null
> }
> ```



### Tool Calling

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "mistralai--mistral-medium-instruct",
    "messages": [
        {
            "role": "system",
            "content": "You are a helpful assistant."
        },
        {
            "role": "user",
            "content": "What is the temperature in Boston today? Tell me in fahrenreit."
        }
    ],
    "tools": [
        {
            "type": "function",
            "function": {
                "name": "get_current_weather",
                "description": "Get the current weather in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city and state, e.g. San Francisco, CA"
                        },
                        "unit": {
                            "type": "string",
                            "enum": [
                                "celsius",
                                "fahrenheit"
                            ]
                        }
                    },
                    "required": [
                        "location"
                    ]
                }
            }
        }
    ],
    "temperature": 0.1,
    "top_p": 0.8,
    "max_tokens": 512
}'
```

> ### Output Code:  
> ```
> {
>   "id": "<id>",
>   "object": "chat.completion",
>   "created": 1757916263,
>   "model": "mistralai--mistral-medium-instruct",
>   "choices": [
>     {
>       "index": 0,
>       "message": {
>         "role": "assistant",
>         "reasoning_content": null,
>         "content": null,
>         "tool_calls": [
>           {
>             "id": "RluueJ6B5",
>             "type": "function",
>             "function": {
>               "name": "get_current_weather",
>               "arguments": "{\"location\": \"Boston, MA\", \"unit\": \"fahrenheit\"}"
>             }
>           }
>         ]
>       },
>       "logprobs": null,
>       "finish_reason": "stop",
>       "stop_reason": null
>     }
>   ],
>   "usage": {
>     "prompt_tokens": 126,
>     "total_tokens": 148,
>     "completion_tokens": 22,
>     "prompt_tokens_details": null
>   },
>   "prompt_logprobs": null
> }
> ```

<a name="concept_kzw_fgm_pgc"/>

<!-- concept\_kzw\_fgm\_pgc -->

## IBM

The `executableId` is `aicore-ibm`



<a name="concept_kzw_fgm_pgc__section_wz3_djx_4gc"/>

## Granite

For more information from the model provider, see [IBM Granite](https://www.ibm.com/docs/en/watsonx/w-and-w/1.1.x?topic=models-granite-13b-chat-v2-model-card).



### ibm--granite-13b-chat

```

curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "<modelName>",
    "messages": [
        {
        "role": "user",
        "content": "Whats the difference between Accountability vs Responsibility, answer in 200 words?"
        }
    ],
    "max_tokens": 100
  }'
```

> ### Output Code:  
> ```
> {
>     "choices": [
>         {
>             "finish_reason": "length",
>             "index": 0,
>             "logprobs": null,
>             "message": {
>                 "content": "Accountability and responsibility are two related but distinct concepts that are often used interchangeably, but they have different nuances. Accountability refers to being answerable or responsible for something, typically for an outcome, decision, or action. It implies that there is a level of ownership and control over the result, and one is expected to take responsibility for the consequences of their actions. Accountability can be held by individuals, teams, or organizations, and it often involves being transparent, communicative, and responsible",
>                 "role": "assistant",
>                 "tool_calls": []
>             },
>             "stop_reason": null
>         }
>     ],
>     "created": 1730097489,
>     "id": "<id>",
>     "model": "<modelName>",
>     "object": "chat.completion",
>     "usage": {
>         "completion_tokens": 100,
>         "prompt_tokens": 24,
>         "total_tokens": 124
>     }
> ```

<a name="concept_k12_1d5_qgc"/>

<!-- concept\_k12\_1d5\_qgc -->

## NVIDIA

The `executableId` is `aicore-nvidia`



## Llama

For more information from the model provider, see [Nvidia](https://build.nvidia.com/nvidia/llama-3_2-nv-embedqa-1b-v2/modelcard).



### nvidia--llama-3.2-nv-embedqa-1b

```
curl --location '$DEPLOYMENT_URL/embeddings' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "input": ["Hello world"],
    "model": "nvidia--llama-3.2-nv-embedqa-1b",
    "input_type": "query",
    "encoding_format": "float",
    "truncate": "NONE"
}'
```

<a name="concept_udz_fgm_pgc"/>

<!-- concept\_udz\_fgm\_pgc -->

## Cohere

The `executableId` is `aicore-cohere`



## Reasoning



### Command A Reasoning

For more information from the model provider, see [Cohere Comman A Reasoning](https://docs.cohere.com/docs/command-a-reasoning).

```
curl --location "$DEPLOYMENT_URL/v2/chat" \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "cohere--command-a-reasoning",
    "stream": false,
    "frequency_penalty": 0.8,
    "thinking": {
        "type": "enabled"
    },
    "messages": [
        {
            "role": "user",
            "content": "Tell me about the reflection?"
        }
    ]
}'
```

<a name="concept_tmp_jwn_zgc"/>

<!-- concept\_tmp\_jwn\_zgc -->

## Perplexity

The `executableId` is `perplexity-ai`



## Completions



### sonar | sonar-pro

> ### Sample Code:  
> ```
> curl --location '$DEPLOYMENT_URL/chat/completions' \
> --header 'AI-Resource-Group: default' \
> --header 'Content-Type: application/json' \
> --heder "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>     "model": "<modelName>",
>     "stream": false,
>     "max_tokens": 20,
>     "messages": [
>       {
>         "role": "system",
>         "content": "You are a powerful business AI assistant."
>       },
>       {
>         "role": "user",
>         "content": "Who is the president of the USA?"
>       }
>     ]
> }'
> ```

