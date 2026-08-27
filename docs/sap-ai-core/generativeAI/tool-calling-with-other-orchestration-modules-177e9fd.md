<!-- loio177e9fd0991a466b831435e64d852d9a -->

# Tool Calling with Other Orchestration Modules

> ### Tip:  
> For use cases including both prompt optimization and tool calling, the `FC:ExactMatch` metric is recommended. Other metrics may return results that are unreliable.



## Data Masking \(Pseudonymization\)

When tool calling is combined with the data masking module it uses the following flow:

1.  **tool\_calls response:** PII in the template is pseudonymized before reaching the LLM. Tool call arguments returned by the LLM contain pseudonymized placeholders \(e.g. `MASKED_PERSON_1`\). The output unmasking step restores the original PII values in the `tool_calls` arguments before returning them to the client.
2.  **stop response:** When you send the unmasked assistant message back \(with original PII in `tool_calls[].function.arguments`\), input masking automatically re-pseudonymizes the arguments before they reach the LLM. The final stop response is then unmasked as usual.

> ### Note:  
> Unmasking of tool call arguments only applies when using `pseudonymization`. With `anonymization`, the original values are irreversibly removed and tool call arguments will contain masked placeholders. Therefore in case of `pseudonymization`, you can safely use them to call your external functions with the original data.



## Content Filtering

When tool calling is combined with the content filtering module it uses the following flow:

1.  **Input filtering:** Filters text content from user, system, and tool messages. Assistant message `content` \(typically empty in tool\_call responses\) is also filtered. However, `tool_calls[].function.arguments` are **not** filtered.
2.  **Output filtering:** Filters the LLM response `content`. Tool call arguments in the response pass through unfiltered.



## Translation

When tool calling is combined with the translation module it uses the following flow:

-   **Input translation:** Translates text content from user, system, and tool messages. Tool call arguments in assistant messages are **not** translated, since they typically contain structured data \(e.g. JSON\) that should not be altered.
-   **Output translation:** Translates the LLM response `content`. For Phase 1 tool\_call responses the content is typically empty, so output translation is effectively a no-op. It becomes meaningful in Phase 2 when the LLM produces a plain-text stop response.

