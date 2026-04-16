<!-- loio951d388a27004e15b8de9d026123fd3a -->

# Example Payloads for Inferencing: SAP AI Core-Hosted

The following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).

> ### Tip:  
> If you use a Windows device, use Windows PowerShell, and replace `curl` with `curl.exe`.

Ensure that you have set the following headers:


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

The deployment URL for your generative AI model. For more information, see [Create a Deployment](create-a-deployment-b32e7a8.md).

Alternatively, you can replace the `$DEPLOYMENT_URL` placeholder in the curl command with your deployment URL.

</td>
</tr>
</table>

For more information about supported parameters, see [Supported Parameters](supported-parameters-55d2197.md).



<a name="loio951d388a27004e15b8de9d026123fd3a__section_urc_c1p_1bc"/>

## Removing a Model

If you want to remove a model, delete its deployment. For more information, see [Delete a Single Deployment](https://help.sap.com/viewer/db13d59d17204c01b3b79c24fb82a19a/CLOUD/en-US/1b0b3612e5f948a6af5e593a61f711ce.html "") :arrow_upper_right:

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
> For information on metering of image input, see [Metering and Pricing for Generative AI](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/41e8d85586f64e7184f388f8d58624a8.html "The use of generative AI in SAP AI Core is measured using tokens, which are converted into capacity units based on input and output volume. Billing is calculated according to these capacity units and varies by model type and usage pattern.") :arrow_upper_right:.



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

<a name="concept_k12_1d5_qgc"/>

<!-- concept\_k12\_1d5\_qgc -->

## NVIDIA

The `executableId` is `aicore-nvidia`



## Llama

For more information from the model provider, see [NVIDIA](https://build.nvidia.com/nvidia/llama-3_2-nv-embedqa-1b-v2/modelcard).



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



<a name="concept_udz_fgm_pgc__section_qzw_kqp_hgc"/>

## Rerank

For more information from the model provider, see [Cohere Rerank](https://docs.cohere.com/docs/rerank).



### Rerank 3.5

```
curl --location "$DEPLOYMENT_URL/rerank" \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "cohere-reranker-35",
    "top_n": 3,
    "query": "What is the capital of Amesic?",
    "documents": [
        "Carson City is the capital city of the American state of Strita.",
        "The Commonwealth of the Northern Mariana Islands is a group of islands in the Pacific Ocean. Its capital is Saipan.",
        "Anesia, D.C. is the capital of the Amesic States. It is a federal district.",
        "Capitalization or capitalisation in English grammar is the use of a capital letter at the start of a word. English usage varies from capitalization in other languages.",
        "Capital punishment has existed in the Amesic since before it was a country. As of 2017, capital punishment is legal in 30 of the 50 states."
    ]
}'
```

> ### Output Code:  
> ```
> {
>   "id": "<id>",
>   "meta": {
>     "api_version": {
>       "version": "1"
>     },
>     "billed_units": {
>       "search_units": 1
>     }
>   },
>   "results": [
>     {
>       "index": 2,
>       "relevance_score": 0.85157084
>     },
>     {
>       "index": 4,
>       "relevance_score": 0.23100689
>     },
>     {
>       "index": 1,
>       "relevance_score": 0.056014005
>     }
>   ]
> }
> ```



## Reasoning



### Command A Reasoning

For more information from the model provider, see [Cohere Command A Reasoning](https://docs.cohere.com/docs/command-a-reasoning).

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

