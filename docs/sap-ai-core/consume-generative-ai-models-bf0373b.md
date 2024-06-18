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
> SAP does not take any responsibility for quality of the content in the input to or output of the underlying generative AI models, including but not limited to, bias, hallucinations, or inaccuracies. The user is responsible for verifying the content.

> ### Caution:  
> Do not store sensitive data in prompts when using the generative AI hub. Sensitive data is any data that is not intended for public disclosure, including but not limited to confidential or personal information.

-   **[Prompt Examples](prompt-examples-543f373.md "")**  


<a name="concept_ynz_mgh_tzb"/>

<!-- concept\_ynz\_mgh\_tzb -->

## Example Payloads for Inferencing

The following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).



<a name="concept_ynz_mgh_tzb__section_d1y_bxc_z1c"/>

## Open AI

For information about the supported API versions, see [Chat completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions) and [Embeddings](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#embeddings) in the Microsoft documentation.



### GPT-4-32k | GPT-4 | GPT-3.5-Turbo-16k | GPT-3.5-Turbo

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



<a name="concept_ynz_mgh_tzb__section_dnb_fxc_z1c"/>

## Falcon

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $TOKEN" \
--data '{
	"model": "tiiuae--falcon-40b-instruct",
	"messages": [
	    {
		"role": "user",
		"content": "sample input prompt"
		}
	],
	"max_tokens": 100
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



<a name="concept_ynz_mgh_tzb__section_ynq_2mt_jbc"/>

## Mistral AI



### mistralai--mixtral-8x7b-instruct-v01

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "mistralai--mixtral-8x7b-instruct-v01",
    "messages": [
        {
        "role": "user",
        "content": "Sample prompt"
        }
    ],
    "max_tokens": 100
  }'
```



<a name="concept_ynz_mgh_tzb__section_kx4_qg4_mbc"/>

## AWS Bedrock



### Claude Sonet | Claude Opus | Claude Haiku

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



<a name="concept_ynz_mgh_tzb__section_jz5_wg4_mbc"/>

## Meta



### LLama-3-70b

```
curl --location '$DEPLOYMENT_URL/chat/completions' \
--header 'AI-Resource-Group: default' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "model": "meta--llama3-70b-instruct",
    "messages": [
        {
        "role": "user",
        "content": "Sample prompt"
        }
    ],
    "max_tokens": 100
  }'
```



If you want to remove a model, delete its deployment. For more information, see [Delete Deployments](delete-deployments-0193d17.md).

