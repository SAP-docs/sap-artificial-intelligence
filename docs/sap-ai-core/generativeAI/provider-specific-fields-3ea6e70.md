<!-- loio3ea6e7027e9f486d8c7502c8c3e5d3b3 -->

# Provider-Specific Fields

The OpenAI Chat Completion schema, which the Orchestration Service follows, defines a fixed set of fields for each choice. Some providers return information that has no direct equivalent in this schema.

Instead of discarding this information, Orchestration returns it in the optional `provider_specific_fields` field of each choice object. This field contains response data that cannot be harmonized with the OpenAI specification while still preserving access to provider-specific information.

In the following example, the model returns a provider-specific finish reason of `end_turn`, which is specific to Anthropic models. Orchestration normalizes this value to the OpenAI-equivalent value `stop` and preserves the original value in `provider_specific_fields`.

```
{
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "Hello!"
      },
      "finish_reason": "stop",
      "provider_specific_fields": {
        "finish_reason": "end_turn"
      }
    }
  ]
}
```



## LLM Provider Finish Reason

The `finish_reason` field in the OpenAI schema supports a limited set of values. Orchestration maps provider-specific stop signals to the closest OpenAI-equivalent value.

This mapping can result in a loss of information. A provider such as Anthropic or Vertex AI can use multiple distinct stop signals that map to the same OpenAI value. Provider-specific signal names can also contain diagnostic information that is not preserved in the normalized value.

When the provider-supplied finish reason differs from the mapped OpenAI value, Orchestration preserves the original value in `provider_specific_fields.finish_reason`. This allows you to inspect the exact stop signal returned by the provider while maintaining compatibility with the normalized `finish_reason` field.

