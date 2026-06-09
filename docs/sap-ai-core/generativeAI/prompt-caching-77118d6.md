<!-- loio77118d6cfc1f49a4944d616ad3bdb9a0 -->

# Prompt Caching

Prompt caching improves performance by reusing predefined sections of a prompt across multiple orchestration requests.

Orchestration supports explicit prompt caching by defining `cache_control` breakpoints on content blocks in the `prompt_templating` module of a request.

Explicit prompt caching is available only in Orchestration V2.

> ### Note:  
> Implicit context caching for OpenAI and Gemini models is enabled by default in orchestration and does not require additional configuration.



## Supported Models

Explicit prompt caching using `cache_control` is supported for the following model families:

-   **Anthropic Claude models** support `cache_control` on `system`, `messages`, and `tools` content blocks. A single request supports up to four cache breakpoints. Cache entries are created in the following order: tools, system, and messages.

-   **Amazon Nova models** support `cache_control` on `system` and `messages` content blocks. A single request typically supports one cache breakpoint.




## Cache TTL \(Time-to-Live\)

By default, cached content uses a five-minute TTL.

```

"cache_control": {"type": "ephemeral"}
      
```

For selected Anthropic Claude models, you can optionally configure a one-hour TTL by setting the `ttl` field.

```

"cache_control": {"type": "ephemeral", "ttl": "1h"}
      
```



## Request Examples

Send a POST request to the following endpoint: **\{\{Orchestration URL\}\}/v2/completion**



## Cache Control on System and Message Content Blocks

The following example shows `cache_control` breakpoints defined on a system message and a user message. This approach is useful when caching long system prompts together with multi-turn few-shot examples.

```

{
  "config": {
    "modules": {
      "prompt_templating": {
        "prompt": {
          "template": [
            {
              "role": "system",
              "content": [
                {
                  "type": "text",
                  "text": "You are an expert news article classifier. Classify each article into exactly one category.",
                  "cache_control": { "type": "ephemeral" }
                }
              ]
            },
            {
              "role": "user",
              "content": "input: Comcast launches prepaid plans"
            },
            {
              "role": "assistant",
              "content": "Business"
            },
            {
              "role": "user",
              "content": "input: Fed signals rate cuts may come later than markets expected"
            },
            {
              "role": "assistant",
              "content": "Economics"
            },
            {
              "role": "user",
              "content": [
                {
                  "type": "text",
                  "text": "input: {{ ?input }}",
                  "cache_control": { "type": "ephemeral" }
                }
              ]
            }
          ]
        },
        "model": {
          "name": "anthropic--claude-4-opus",
          "params": {
            "max_tokens": 50,
            "temperature": 0.1
          }
        }
      }
    }
  },
  "placeholder_values": {
    "input": "Scaling up neural models has yielded significant advancements in language generation"
  }
}
      
```



## Cache Control on Tools \(Anthropic Claude Only\)

You can also apply `cache_control` to tool definitions. Add the `cache_control` field at the same level as `type` and `function`.

```

"tools": [
  {
    "type": "function",
    "function": {
      "name": "classify_article",
      "description": "Classify a news article into a predefined category.",
      "parameters": {
        "type": "object",
        "properties": {
          "category": {
            "type": "string",
            "enum": ["Business", "Economics", "Tech"],
            "description": "The primary category of the article"
          }
        },
        "required": ["category"]
      }
    },
    "cache_control": { "type": "ephemeral" }
  }
]
      
```



## Amazon Nova Models

For Amazon Nova models, use the same `cache_control` syntax. The orchestration service automatically converts `cache_control` to the native Nova cachePoint format.

```

"model": {
  "name": "amazon--nova-pro",
  "params": {
    "max_tokens": 200
  }
}
      
```

> ### Note:  
> Amazon Nova models support cache control only on system and messages content blocks. Cache control on tools and explicit TTL values is not supported.



## Response

When prompt caching is enabled, the response usage object includes additional fields in `prompt_tokens_details` to report cache usage.



## Response with Cache Usage Using Default Time to Live

When cache\_control is used without an explicit time-to-live value, the response includes both cached\_tokens and cache\_creation\_tokens in the prompt\_tokens\_details object.

```

{
  "usage": {
    "completion_tokens": 4,
    "prompt_tokens": 3,
    "total_tokens": 7,
    "prompt_tokens_details": {
      "cached_tokens": 4657,
      "cache_creation_tokens": 0
    }
  }
}
      
```

`cached_tokens` indicates the number of input tokens read from the cache.

`cache_creation_tokens` indicates the number of input tokens written to the cache.



## Response with Cache Usage Using Explicit Time to Live

When cache\_control includes an explicit time-to-live value, the response adds cache\_creation\_token\_details to show a breakdown of cached tokens by duration.

```

{
  "usage": {
    "completion_tokens": 4,
    "prompt_tokens": 3,
    "total_tokens": 7,
    "prompt_tokens_details": {
      "cached_tokens": 4657,
      "cache_creation_tokens": 0,
      "cache_creation_token_details": {
        "ephemeral_5m_input_tokens": 0,
        "ephemeral_1h_input_tokens": 0
      }
    }
  }
}
      
```

`ephemeral_5m_input_tokens` represents tokens cached with a five-minute duration.

`ephemeral_1h_input_tokens` represents tokens cached with a one-hour duration.



## Limitations

Explicit prompt caching using cache\_control is supported only for Anthropic Claude models and Amazon Nova models.

Amazon Nova models do not support cache\_control on tools content blocks.

The one-hour time-to-live value is supported only by select Anthropic models.

Prompt caching requires a minimum number of tokens in the prompt prefix. If the prompt is too short, the cache breakpoint may not take effect. For more information, see the Anthropic prompt caching documentation at [https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching) and the Amazon Bedrock prompt caching documentation at [https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-caching.html](https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-caching.html).

