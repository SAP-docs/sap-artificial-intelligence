<!-- loiob66b8a0e9d934db2b437da52667cb7f3 -->

# Reasoning

> ### Note:  
> `reasoning_content` is only available in Orchestration V2.

Orchestration supports models with reasoning capabilities. Reasoning is harmonized across all supported providers under a unified API specification, independent of the underlying model's native format.



## Enabling Reasoning

To enable reasoning, set the `reasoning_effort` parameter in the model configuration. When set, the model is instructed to perform reasoning before producing a response.

The following values are supported:

-   `"minimal"`
-   `"low"`
-   `"medium"`
-   `"high"`
-   `"none"` \(disables reasoning when possible\)

> ### Note:  
> Not all models support the full range of configuration options. Where possible, orchestration maps unsupported values to the closest equivalent. For example, `"minimal"`, `"low"` and `"medium"` are mapped to`"high"` for `mistralai--mistral-small` because the model only supports `"none"` or `"high"`.



## Reasoning Content

When a model performs reasoning, orchestration returns the progress in the `reasoning_content` field.

**Response Format**

> ### Output Code:  
> ```
> {
>   "choices": [
>     {
>       "message": {
>         "role": "assistant",
>         "content": "The answer is 42.",
>         "reasoning_content": [
>           {
>             "content": "Let me think through this step by step...",
>             "signature": "CiUBjz1rX..."
>           }
>         ]
>       }
>     }
>   ]
> }
> 
> ```

Each reasoning block has two fields:


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`content`

</td>
<td valign="top">

The reasoning text produced by the model.

</td>
</tr>
<tr>
<td valign="top">

`signature`

</td>
<td valign="top">

An opaque string required to replay reasoning in follow-up requests. May be an empty, as not all models return a signature.

</td>
</tr>
</table>

> ### Note:  
> Not all reasoning models expose their internal reasoning processes. Reasoning content is returned whenever the model provides it.



## Streaming

In streaming responses, reasoning content is spread across multiple chunks. The `signature` may appear in a different chunk than the `content`, depending on the model. Always accumulate all `reasoning_content` blocks across all chunks before using them in a follow-up request.

```
{
  "choices": [
    {
      "delta": {
        "role": "assistant",
        "content": "",
        "reasoning_content": [
          {
            "content": "Let me think through this step by step...",
            "signature": ""
          }
        ]
      }
    }
  ]
}

```

A later chunk may carry the signature with empty content:

```
{
  "choices": [
    {
      "delta": {
        "role": "assistant",
        "content": "",
        "reasoning_content": [
          {
            "content": "",
            "signature": "CiUBjz1rX..."
          }
        ]
      }
    }
  ]
}

```



## Multi-Turn Conversations

When continuing a conversation, always include the full list `reasoning_content` blocks from the previous assistant message in messages\_history **exactly as returned by the API**.

-   **Do not modify** the `content` or `signature` fields.
-   **Do not omit** reasoning blocks, even if they have an empty `content` or `signature`.
-   **Do not merge** multiple blocks into one.

Returning reasoning content generally improves model accuracy and is recommended for all providers.

> ### Note:  
> For Anthropic models, it is **strictly required** when tool calls are present in the same assistant turn.

> ### Sample Code:  
> ```
> {
>   "config": {
>     "modules": {
>       "prompt_templating": {
>         "prompt": {
>           "template": [
>             { "role": "user", "content": "Are you sure?" }
>           ]
>         },
>         "model": {
>           "name": "anthropic--claude-4-sonnet",
>           "params": { "reasoning_effort": "medium" }
>         }
>       }
>     }
>   },
>   "messages_history": [
>     { "role": "user", "content": "What is 6 times 7?" },
>     {
>       "role": "assistant",
>       "content": "The answer is 42.",
>       "reasoning_content": [
>         {
>           "content": "6 times 7 equals 42.",
>           "signature": "CiUBjz1rX..."
>         }
>       ]
>     }
>   ]
> }
> 
> ```

