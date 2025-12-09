<!-- loio8c80ea225b094cf999d8de11e5eb2850 -->

# Example Payloads for Inferencing - Remote Models

The following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).

> ### Tip:  
> If you use a Windows device, use Windows Powershell, and replace `curl` with `curl.exe`.

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

The deployment URL for your generative AI model. For more information, see [Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-b32e7a8.md).

Alternatively, you can replace the `$DEPLOYMENT_URL` placeholder in the curl command with your deployment URL.

</td>
</tr>
</table>

For more information about supported parameters, see [Supported Parameters](supported-parameters-55d2197.md).



If you want to remove a model, delete its deployment. For more information, see [Delete a Single Deployment](delete-a-single-deployment-1b0b361.md) and [Delete Multiple Deployments](delete-multiple-deployments-6b521aa.md).

<a name="concept_u3x_41m_pgc"/>

<!-- concept\_u3x\_41m\_pgc -->

## Open AI

The `executableId` is `azure-openai`.



<a name="concept_u3x_41m_pgc__section_d1y_bxc_z1c"/>

## Completions

For more information from the model provider, see [Microsoft Azure Open AI Chat Completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions).



### gpt-4-32k | gpt-4 | gpt-3.5-Turbo-16k | gpt-3.5-Turbo | o4-mini | o3 | gpt-4.1 | gpt-4.1-mini | gpt-4.1-nano | gpt-5 | gpt-5-mini | gpt-5-nano

**Text Input**

```
curl --location '$DEPLOYMENT_URL/chat/completions?api-version=2023-05-15' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "messages": [
        {
            "role": "user",
            "content": "sample input prompt"
        }
    ],
    "max_tokens": 100,
    "temperature": 0,
    "frequency_penalty": 0,
    "presence_penalty": 0,
    "stop": "null"
}'
```



### **o1 | o3-mini**

```
curl --location '$DEPLOYMENT_URL/chat/completions?api-version=2024-12-01-preview' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "messages": [
      {
        "role": "user",
        "content": "Hello!"
      }
    ]
  }'
```



### GPT-4o | GPT-4-Turbo | GPT-4o Mini

Image input

```

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



<a name="concept_u3x_41m_pgc__section_eq3_wbm_pgc"/>

## Embeddings

For more information from the model provider, see [Microsoft Azure Open AI Embeddings](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#embeddings).



### text-embedding-ada-002 | text-embedding-3-small | text-embedding-3-large

```
curl --location '$DEPLOYMENT_URL/embeddings?api-version=2023-05-15' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
	"input": "sample input prompt"
}'
```

<a name="concept_kgh_q1m_pgc"/>

<!-- concept\_kgh\_q1m\_pgc -->

## Vertex AI

The `executableId` is `gcp-vertexai`.



<a name="concept_kgh_q1m_pgc__section_p3k_fxc_z1c"/>

## Gemini

For more information from the model provider, see [Vertex AI Gemini](https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/inference).



### Gemini 2.0 Flash | Gemini 2.0 Flash Lite | Gemini 2.5 Flash | Gemini 2.5 Flash Lite

**Text Input**

```
curl --request POST --location "$DEPLOYMENT_URL/models/<modelName>:generateContent" \ #example gemini-1.5-flash:generateContent
--header 'AI-Resource-Group: <Resource Group Id>' \
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
curl --request POST --location "$DEPLOYMENT_URL/models/<modelVersion>:generateContent" \ #example gemini-1.5-flash:generateContent
--header 'AI-Resource-Group: <Resource Group Id>' \
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



### Gemini Embedding

```
curl --location '$DEPLOYMENT_URL/models/gemini-embedding:predict' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
  "instances": [
    { 
      "task_type": "<Task Type>",
      "title": "Behaviour Analysis",
      "content": "What is quid pro quo?"
    }
  ]
}'
```

`Task_type` can take the following values:

-   `RETRIEVAL_QUERY`
-   `RETRIEVAL_DOCUMENT`
-   `SEMANTIC_SIMILARITY`
-   `CLASSIFICATION`
-   `CLUSTERING`

<a name="concept_zk1_r1m_pgc"/>

<!-- concept\_zk1\_r1m\_pgc -->

## AWS Bedrock

The `executableId` is `aws-bedrock`.



<a name="concept_zk1_r1m_pgc__section_kx4_qg4_mbc"/>

## Anthropic Claude

For more information from the model provider, see [AWS Bedrock Claude](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-claude.html).



### Claude 3 Sonnet | Claude 3.5 Sonnet | Claude 3 Opus | Claude 3 Haiku | Claude 4 Sonnet | Claude 4 Opus || Claude 4.5 Haiku

**Invoke:**

```
curl --location '$DEPLOYMENT_URL/invoke' \
--header 'AI-Resource-Group: <Resource Group Id>' \
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

**Converse:**

```
curl --location '$DEPLOYMENT_URL/converse' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "inferenceConfig": {
        "maxTokens": 100,
        "stopSequences": [
            "blab"
        ],
        "temperature": 0.7
    },
    "messages": [
        {
            "content": [
                {
                    "text": "Perplexity means?"
                }
            ],
            "role": "user"
        }
    ]
}'

```



### Claude 3.7 Sonnet

```
curl --location '$DEPLOYMENT_URL/converse' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "inferenceConfig": {
        "maxTokens": 100,
        "stopSequences": [
            "blab"
        ],
        "temperature": 0.7
    },
    "messages": [
        {
            "content": [
                {
                    "text": "Perplexity means?"
                }
            ],
            "role": "user"
        }
    ]
}'
```



<a name="concept_zk1_r1m_pgc__section_hsp_wdm_pgc"/>

## Amazon Titan

For more information from the model provider, see [AWS Bedrock Titan](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-titan.html).



### Titan Text Express | Titan Text Lite

```
curl --location '$DEPLOYMENT_URL/invoke' \
--header 'AI-Resource-Group: <Resource Group Id>' \
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
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "inputText": "Who im I?"
  }'
```



### Titan Embed Image

```
curl --location '$DEPLOYMENT_URL/invoke' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "inputText": "hi",
    "inputImage": "#this-is-an-example-base64-string-value for-an-image/9j/4QDeRXhpZgAASUkqAAgAAAAGABIBAwABAAAAAQAAABoBBQABAAAAVgAAABsBBQABAAAAXgAAACgBAwABAAAAAgAAABMCAwABAAAAAQAAAGmHBAABAAAAZgAAAAAAAABIAAAAAQAAAEgAAAABAAAABwAAkAcABAAAADAyMTABkQcABAAAAAECAwCGkgcAFgAAAMAAAAAAoAcABAAAADAxMDABoAMAAQAAAP//AAACoAQAAQAAAMgAAAADoAQAAQAAAMgAAAAAAAAAQVNDSUkAAABQaWNzdW0gSUQ6IDEyM//bAEMACAYGBwYFCAcHBwkJCAoMFA0MCwsMGRITDxQdGh8eHRocHCAkLicgIiwjHBwoNyksMDE0NDQfJzk9ODI8LjM0Mv/bAEMBCQkJDAsMGA0NGDIhHCEyMjIyMjIyMjIyMjIyM",
    "embeddingConfig": {
        "outputEmbeddingLength": 256
    }
}'

```

> ### Output Code:  
> ```
> {
>   "embedding": [
>     -0.0013275146,
>     -0.024658203,
>     ...
>     0.068359375,
>     0.014404297,
>     0.025512695
>   ],
>   "inputTextTokenCount": 3
> }
> ```



<a name="concept_zk1_r1m_pgc__section_v4j_ydm_pgc"/>

## Amazon Nova

For more information from the model provider, see [AWS Bedrock Nova](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-nova.html).



### Nova Pro | Nova Lite | Nova Micro | Nova Premier

```
curl --location '$DEPLOYMENT_URL/converse' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "inferenceConfig": {
        "maxTokens": 100,
        "stopSequences": [
            "blab"
        ],
        "temperature": 0.7
    },
    "messages": [
        {
            "content": [
                {
                    "text": "Perplexity means?"
                }
            ],
            "role": "user"
        }
    ]
}'
```



## Streaming

Where supported, streaming for Amazon Bedrock models can be invoked by replacing the deployment URL with `$DEPLOYMENT_URL/invoke-with-response-stream`.

