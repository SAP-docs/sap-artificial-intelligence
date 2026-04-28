<!-- loio17d02acff0d14bf8aedfd53a473ff8fc -->

# Cohere



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
-   The `executableId`: `aicore-cohere`

-   The name of your chosen model
-   The version name of your chosen version. If no model version is listed, it is not applicable.

To use a specific version of a model, or to upgrade model versions manually, specify the model version your model deployment. To upgrade automatically, use model version: `latest`. For more information, see [Model Lifecycle](model-lifecycle-313fe25.md). If no model version is listed, it is not applicable.

Cohere model is SAP AI Core hosted.

For more information from the model provider, see [Cohere Rerank](https://docs.cohere.com/docs/rerank).

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



<a name="loio17d02acff0d14bf8aedfd53a473ff8fc__consumption"/>

## Consumption

The following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).

> ### Tip:  
> If you use a Windows device, use Windows PowerShell, and replace `curl` with `curl.exe`.

For more information about supported parameters, see [Supported Parameters](supported-parameters-55d2197.md).



<a name="loio17d02acff0d14bf8aedfd53a473ff8fc__section_qzw_kqp_hgc"/>

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



<a name="loio17d02acff0d14bf8aedfd53a473ff8fc__section_urc_c1p_1bc"/>

## Removing a Model

If you want to remove a model, delete its deployment. For more information, see [Delete a Single Deployment](https://help.sap.com/viewer/db13d59d17204c01b3b79c24fb82a19a/CLOUD/en-US/1b0b3612e5f948a6af5e593a61f711ce.html "") :arrow_upper_right:

