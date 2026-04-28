<!-- loio6a81f85100fe4ecd94a056137b43a696 -->

# AWS Bedrock



## Context

You can access LLMs through the `foundation-models` and `orchestration` scenarios.

To use a model through the `orchestration` scenario, using the harmonized API, see [Orchestration](orchestration-8d02235.md).

**For more information about available models, including conversion rates for tokens, rate limits and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**



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
-   The `executableId`: `aws-bedrock`

-   The name of your chosen model
-   The version name of your chosen version. If no model version is listed, it is not applicable.

To use a specific version of a model, or to upgrade model versions manually, specify the model version your model deployment. To upgrade automatically, use model version: `latest`. For more information, see [Model Lifecycle](model-lifecycle-313fe25.md). If no model version is listed, it is not applicable.

After creating a deployment for your model, you consume the model using prompts. To access the model, you'll need your deployment ID, this can be set as an environment variable.

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



<a name="loio6a81f85100fe4ecd94a056137b43a696__consumption"/>

## Consumption

The following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).

> ### Tip:  
> If you use a Windows device, use Windows PowerShell, and replace `curl` with `curl.exe`.

For more information about supported parameters, see [Supported Parameters](supported-parameters-55d2197.md).



<a name="loio6a81f85100fe4ecd94a056137b43a696__section_kx4_qg4_mbc"/>

## Anthropic Claude

For more information from the model provider, see [AWS Bedrock Claude](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-claude.html).



### Claude 3 Haiku | Claude 3.5 Sonnet | Claude 4 Sonnet | Claude 4 Opus | Claude 4.5 Haiku | Claude 4.5 Sonnet | Claude 4.6 Opus | Claude 4 Sonnet

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



<a name="loio6a81f85100fe4ecd94a056137b43a696__section_hsp_wdm_pgc"/>

## Amazon Titan

For more information from the model provider, see [AWS Bedrock Titan](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-titan.html).



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



<a name="loio6a81f85100fe4ecd94a056137b43a696__section_v4j_ydm_pgc"/>

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



<a name="loio6a81f85100fe4ecd94a056137b43a696__section_urc_c1p_1bc"/>

## Removing a Model

If you want to remove a model, delete its deployment. For more information, see [Delete a Single Deployment](https://help.sap.com/viewer/db13d59d17204c01b3b79c24fb82a19a/CLOUD/en-US/1b0b3612e5f948a6af5e593a61f711ce.html "") :arrow_upper_right:

