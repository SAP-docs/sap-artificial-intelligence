<!-- loio6ab293a5792e4a27ab6ce10579d47976 -->

# Mistral



## Context

You can access LLMs through the `foundation-models` and `orchestration` scenarios.

To use a model through the `orchestration` scenario, using the harmonized API, see [Orchestration](orchestration-8d02235.md).

**For more information about available models, including conversion rates for tokens, rate limits, and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**



## Accessing Models through Orchestration

Orchestration offers a harmonized API that allows you to use different models without changing the client code. You likely have an orchestration deployment running in your default resource group. If you want to access models through orchestration in a different resource group, you'll need to create an orchestration deployment for your chosen resource group. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).

Access to orchestration of generative AI models is provided under the global AI scenario `orchestration`, which is managed by SAP AI Core.

To access generative AI models using orchestration, you'll need to add following information to the `model` module of your orchestration workflow:

-   The name of your chosen model
-   The version name of your chosen version. If no model version is listed, it is not applicable.

For more information about supported models and associated costs, see SAP Note [3505347](https://me.sap.com/notes/3505347)

For more information about orchestration workflows, see [Orchestration Workflow V2](orchestration-workflow-v2-41a0247.md).



## Accessing Models through Orchestration

Orchestration offers a harmonized API that allows you to use different models without changing the client code. You likely have an orchestration deployment running in your default resource group. If you want to access models through orchestration in a different resource group, you'll need to create an orchestration deployment for your chosen resource group. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).

Access to orchestration of generative AI models is provided under the global AI scenario `orchestration`, which is managed by SAP AI Core.

To access generative AI models using orchestration, you'll need to add following information to the `model` module of your orchestration workflow:

-   The name of your chosen model
-   The version name of your chosen version. If no model version is listed, it is not applicable.

For more information about supported models and associated costs, see SAP Note [3505347](https://me.sap.com/notes/3505347)

For more information about orchestration workflows, see [Orchestration Workflow V2](orchestration-workflow-v2-41a0247.md).



## Accessing Models through the `foundation-models` Scenario

You can access foundation models by creating a deployment for the model that you want to use. To do this, you'll need an auth token from your SAP AI Core instance. For more information, see [Get an Auth Token](get-an-auth-token-0808d42.md) and [Create a Deployment](create-a-deployment-b32e7a8.md).

To create your deployment, you'll need the following information:

-   The scenario: `foundation-models`
-   The `executableId`: `aicore-mistralai`

-   The name of your chosen model
-   The version name of your chosen version. If no model version is listed, it is not applicable.

To use a specific version of a model, or to upgrade model versions manually, specify the model version your model deployment. To upgrade automatically, use model version: `latest`. For more information, see [Model Lifecycle](model-lifecycle-313fe25.md). If no model version is listed, it is not applicable.

Mistral models are SAP AI Core hosted.

For more information from the model provider, see [Mistral Large](https://huggingface.co/mistralai/Mistral-Large-Instruct-2407) and [Mistral Small](https://huggingface.co/mistralai/Mistral-Small-3.1-24B-Instruct-2503).

After creating a deployment for your model, you consume the model using prompts. To access the model, you'll need your deployment ID, this can be set as an environment variable.

Ensure that you've set the following headers:


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



<a name="loio6ab293a5792e4a27ab6ce10579d47976__consumption"/>

## Consumption

The following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).

> ### Tip:  
> If you use a Windows device, use Windows PowerShell, and replace `curl` with `curl.exe`.

For more information about supported parameters, see [Supported Parameters](supported-parameters-55d2197.md).



<a name="loio6ab293a5792e4a27ab6ce10579d47976__section_uz3_djx_4gc"/>

## mistralai--mistral-large-instruct | mistralai--mistral-small-instruct| mistralai--mistral-small

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
>   "choices": [
>     {
>       "finish_reason": "length",
>       "index": 0,
>       "logprobs": null,
>       "message": {
>         "annotations": null,
>         "audio": null,
>         "content": "**Accountability vs. Responsibility**\n\nWhile often used interchangeably, **responsibility** and **accountability** have distinct meanings in personal and professional contexts.\n\n**Responsibility** refers to the obligation to perform a task or role. It is about **what** you are expected to do—your duties, tasks, or assignments. For example, a manager is *responsible* for leading a team or overseeing a project. Responsibility is assigned (e.g., job descriptions, contracts) and does not necessarily imply consequences for outcomes.\n\n**Accountability**, on the other hand, is about **answering for results**. It involves taking ownership of outcomes, whether successful or not, and being prepared to explain, justify, or face consequences. Accountability requires transparency, integrity, and a willingness to learn from mistakes. For instance, if a project fails, an *accountable* person does not shift blame but explains what went wrong and how to improve.\n\nIn essence:\n- **Responsibility** = *Doing* the work.\n- **Accountability** = *Answering* for the work’s results.\n\nA person can be *responsible* without being *accountable* if they delegate tasks without oversee",
>         "function_call": null,
>         "reasoning": null,
>         "refusal": null,
>         "role": "assistant",
>         "tool_calls": []
>       },
>       "stop_reason": null,
>       "token_ids": null
>     }
>   ],
>   "created": 1777541318,
>   "id": "chatcmpl-963fc89d2548ada6",
>   "kv_transfer_params": null,
>   "model": "mistralai--mistral-small",
>   "object": "chat.completion",
>   "prompt_logprobs": null,
>   "prompt_token_ids": null,
>   "service_tier": null,
>   "system_fingerprint": null,
>   "usage": {
>     "completion_tokens": 250,
>     "prompt_tokens": 30,
>     "prompt_tokens_details": null,
>     "total_tokens": 280
>   }
> }
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



<a name="loio6ab293a5792e4a27ab6ce10579d47976__section_urc_c1p_1bc"/>

## Removing a Model

If you want to remove a model, delete its deployment. For more information, see [Delete a Single Deployment](https://help.sap.com/viewer/db13d59d17204c01b3b79c24fb82a19a/CLOUD/en-US/1b0b3612e5f948a6af5e593a61f711ce.html "") :arrow_upper_right:

