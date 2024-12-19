<!-- loiobf0373b1cf2a4680a7044e1a562d3853 -->

# Consume Generative AI Models

The generative AI hub helps you to complete tasks like summarizing text, inferencing, and transforming content. To do so, you consume a generative AI model by sending a request to the model's endpoint.



<a name="loiobf0373b1cf2a4680a7044e1a562d3853__prereq_nzn_mdw_tyb"/>

## Prerequisites

You have the deployment URL for your generative AI model. For more information, see [Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-b32e7a8.md).



<a name="loiobf0373b1cf2a4680a7044e1a562d3853__context_wb4_2fc_zyb"/>

## Context

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

Bearer $TOKEN

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
</table>

> ### Caution:  
> SAP does not take any responsibility for quality of the content in the input to or output of the underlying generative AI models. This includes but is not limited to bias, hallucinations, or inaccuracies. The user is responsible for verifying the content.

> ### Caution:  
> Do not store personally identifiable information in prompts when using the generative AI hub. Personally identifiable information is any data that can be used alone, or in combination, to identify the person that the data refers to.

-   **[Prompt Examples](prompt-examples-543f373.md "")**  


<a name="concept_ynz_mgh_tzb"/>

<!-- concept\_ynz\_mgh\_tzb -->

## Example Payloads for Inferencing

llama2-70b-chat-hfThe following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).

> ### Tip:  
> If you use a Windows device, use Windows Powershell, and replace `curl` with `curl.exe`.



<a name="concept_ynz_mgh_tzb__section_d1y_bxc_z1c"/>

## Open AI

For information about the supported API versions, see [Chat completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions) and [Embeddings](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#embeddings) in the Microsoft documentation.



### GPT-4-32k | GPT-4 | GPT-3.5-Turbo-16k | GPT-3.5-Turbo

**Text Input**

```
curl --location '$DEPLOYMENT_URL/chat/completions?api-version=2023-05-15' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
	"messages": [
	    {
		"role": "user",
		"content": "sample input prompt"
		}
	],
	"max_tokens": 100,
	"temperature": 0.0,
	"frequency_penalty": 0,
	"presence_penalty": 0,
	"stop": "null"
}'
```



### GPT-4o | GPT-4-Turbo | GPT-4o Mini

**Image input**

```
# Request
# ---
curl --location '$DEPLOYMENT_URL/chat/completions?api-version=2023-05-15' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "messages": [
      {
        "role": "user",
        "content": [
           {
              "type": "text",
              "text": "Describe this picture:"
           },
           {
              "type": "image_url",
              "image_url": {
                 "url": "https://path/images/image.png"
              }
          }
        ]
      }
    ],
    "max_tokens": 10
}'
```



### text-embedding-ada-002 | text-embedding-3-small | text-embedding-3-large

```
curl --location '$DEPLOYMENT_URL/embeddings?api-version=2023-05-15' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
	"input": "sample input prompt"
}'
```



<a name="concept_ynz_mgh_tzb__section_p3k_fxc_z1c"/>

## Vertex AI



### Gemini 1.0 Pro

```
curl --location '$DEPLOYMENT_URL/models/gemini-1.0-pro:generateContent' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
	"contents": [ 
		{
		"role": "user", 
		"parts": { "text": "Hello!" } 
		}, 
		{
		"role": "model", 
		"parts": { "text": "Argh! What brings ye to my ship?" }
		},
		{ "role": "user",
		"parts": { "text": "Wow! You are a real-life pirate!" }
		}
		],
	"safety_settings": {
		"category": "HARM_CATEGORY_SEXUALLY_EXPLICIT",
		"threshold": "BLOCK_LOW_AND_ABOVE" 
		},
	"generation_config": { 
		"temperature": 0.9, 
		"topP": 1, 
		"candidateCount": 1, 
		"maxOutputTokens": 2048
		}
}'
```



### Gemini 1.5 Pro

**Text Input**

```
curl --location '$DEPLOYMENT_URL/models/gemini-1.5-pro:generateContent' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
    "generation_config":{
        "maxOutputTokens":100
    }, 
    "contents": {
      "role": "user",
      "parts": {
          "text": "Give me a recipe for banana bread."
       }
      },
    "safety_settings": {
      "category": "HARM_CATEGORY_SEXUALLY_EXPLICIT",
      "threshold": "BLOCK_LOW_AND_ABOVE"
    }
}'
```

**Image input**

```
curl --request POST --location "$DEPLOYMENT_URL/models/gemini-1.5-pro:generateContent" \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "contents": {
      "role": "user",
      "parts": [
        {
        "fileData": {
          "mimeType": "image/png",
          "fileUri": "filepath/images/scones.jpg"
          }
        },
        {
          "text": "Describe this picture."
        }
      ]
    }
}'
```



### Gemini 1.5 Flash

**Text Input**

```
curl --request POST --location "$DEPLOYMENT_URL/models/gemini-1.5-flash:generateContent" \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "generation_config":{
        "maxOutputTokens":100
    }, 
    "contents": {
      "role": "user",
      "parts": {
          "text": "Give me a recipe for banana bread."
       }
      },
    "safety_settings": {
      "category": "HARM_CATEGORY_SEXUALLY_EXPLICIT",
      "threshold": "BLOCK_LOW_AND_ABOVE"
    }
}'
```

**Image input**

```
curl --request POST --location "$DEPLOYMENT_URL/models/gemini-1.5-flash:generateContent" \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "contents": {
      "role": "user",
      "parts": [
        {
        "fileData": {
          "mimeType": "image/png",
          "fileUri": "filepath/images/scones.jpg"
          }
        },
        {
          "text": "Describe this picture."
        }
      ]
    }
}'
```



### Text Bison

```
curl --location '$DEPLOYMENT_URL/models/text-bison:predict'  \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
	"instances": [
	{
	      "prompt": "Sample prompt"
	    }
	],
	"parameters": {
	"temperature": 0.8,
	"maxOutputTokens": 50
	}
}'
```



### Chat Bison

```
curl --location '$DEPLOYMENT_URL/models/chat-bison:predict'  \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
	"instances": [
    {
      "context": "Your conversation context here",
      "messages": [
        {
          "author": "user",
          "content": "User message 1"
        },
        {
          "author": "assistant",
          "content": "Assistant response 1"
        },
        {
          "author": "user",
          "content": "User message 2"
        }
      ]
    }
  ],

	"parameters": {
	"temperature": 0.8
	}
}'
```



### Textembedding Gecko

```
curl --location '$DEPLOYMENT_URL/models/textembedding-gecko:predict'  \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
	"instances": [
    {
      "task_type": "RETRIEVAL_DOCUMENT",
      "title": "Document title",
      "content": "I would like embeddings for this text"
    }
  ]
}'
```



### Textembedding Gecko Multilingual

```
curl --location '$DEPLOYMENT_URL/models/textembedding-gecko-multilingual:predict'  \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
	"instances": [
		{
		"task_type": "RETRIEVAL_DOCUMENT",
		"title": "Document title",
		"content": "I would like embeddings for this text"
		}
	]
}'
```



<a name="concept_ynz_mgh_tzb__section_kx4_qg4_mbc"/>

## AWS Bedrock



### Claude 3 Sonnet | Claude 3.5 Sonnet |Claude 3 Opus | Claude 3 Haiku

```
curl --location '$DEPLOYMENT_URL/invoke' \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "anthropic_version": "bedrock-2023-05-31",
    "max_tokens": 100,
    "messages": [
        {
        "role": "user", 
        "content": "Hello, Claude"
        }
    ]
  }'
```



### Titan Text Express | Titan Text Lite

```
curl --location '$DEPLOYMENT_URL/invoke' \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "inputText": "Who am AI?",
    "textGenerationConfig": {
        "maxTokenCount": 10,
        "stopSequences": [],
        "temperature": 0,
        "topP": 1
     }
   }'
```



### Titan Embed Text

```
curl --location '$DEPLOYMENT_URL/invoke' \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "inputText": "Who im I?"
  }'
```



### Nova Pro | Nova Lite | Nova Micro

```
curl --location '$DEPLOYMENT_URL/converse' \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
   "inferenceConfig": { 
      "maxTokens": 100,
      "stopSequences": [ "blab" ],
      "temperature": 0.7
   },
   "messages": [ 
      { 
         "content": [ { 
           "text": "Perplexity means?" 
         }],
         "role": "user"
      }
   ]
}'
```



<a name="concept_ynz_mgh_tzb__section_nmg_5rx_rcc"/>

## aicore-opensource



### Llama-3-70b-instruct| Llama-3.1-70b-instruct | mistralai--mixtral-8x7b-instruct-v01

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: default' \
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



<a name="concept_ynz_mgh_tzb__section_hj4_yjh_tcc"/>

## aicore-mistral



### mistralai--mistral-large-instruct

```

curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: default' \
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


# Here's an example response:
{
    "choices": [
        {
            "finish_reason": "length",
            "index": 0,
            "logprobs": null,
            "message": {
                "content": " Accountability and responsibility are related but distinct concepts.\n\n**Responsibility** is about the tasks and duties assigned to you. It's what you're expected to do as part of your role or agreement. For example, a project manager is responsible for planning and overseeing a project. Responsibility is often proactive and focuses on what you should do.\n\n**Accountability**, on the other hand, is about answering for the outcomes of your responsibilities. It",
                "role": "assistant",
                "tool_calls": []
            },
            "stop_reason": null
        }
    ],
    "created": 1730096376,
    "id": "chat-8f06fb250621420a9aa1baafadb04da1",
    "model": "mistralai--mistral-large-instruct",
    "object": "chat.completion",
    "usage": {
        "completion_tokens": 100,
        "prompt_tokens": 23,
        "total_tokens": 123
    }
```



<a name="concept_ynz_mgh_tzb__section_zy1_bgy_wcc"/>

## aicore-ibm



### ibm--granite-13b-chat

```

curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: default' \
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


# Here's an example response:
{
    "choices": [
        {
            "finish_reason": "length",
            "index": 0,
            "logprobs": null,
            "message": {
                "content": "Accountability and responsibility are two related but distinct concepts that are often used interchangeably, but they have different nuances. Accountability refers to being answerable or responsible for something, typically for an outcome, decision, or action. It implies that there is a level of ownership and control over the result, and one is expected to take responsibility for the consequences of their actions. Accountability can be held by individuals, teams, or organizations, and it often involves being transparent, communicative, and responsible",
                "role": "assistant",
                "tool_calls": []
            },
            "stop_reason": null
        }
    ],
    "created": 1730097489,
    "id": "chat-9acb599c079248f59281238c6d5c1a30",
    "model": "ibm--granite-13b-chat",
    "object": "chat.completion",
    "usage": {
        "completion_tokens": 100,
        "prompt_tokens": 24,
        "total_tokens": 124
    }
```



If you want to remove a model, delete its deployment. For more information, see [Delete a Single Deployment](delete-a-single-deployment-1b0b361.md) and [Delete Multiple Deployments](delete-multiple-deployments-6b521aa.md).

