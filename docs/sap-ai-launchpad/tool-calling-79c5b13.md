<!-- loio79c5b130ac5d4bc5bc13c82c43905c7f -->

# Tool Calling

You can incorporate specialist tools into your orchestration workflow for example to make an API call for current data or to execute custom code. LLMs decide that a tool call is needed based on your system prompt, messages and tool definition.

You can define multiple tools, and use the decision making capabilities of generative AI models to guide you in their use.

Only function call type tools are supported.

Function calling is helpful for agentic use cases where the LLM determines which tool to use out of a provided selection of tools. The LLM determines which tool is best for the use case, but the tool needs to be called separately in the application.

For more information, see [Tool Calling in SAP AI Core](https://help.sap.com/docs/AI_CORE/7d01240443d84db6890f318fe5d1123f/2e478712a9794bc1b0a6f95f60060fc7.html).

**Example**

```
[
  {
    "id": "toolu_bdrk_013CkB5QCHc2ZpfwwoBkqZC6",
    "type": "function",
    "function": {
      "name": "get_order_status",
      "arguments": "{\"order_id\": \"98231\"}"
    }
  }
]
       
```

The tool calling module returns tools that are appropriate for your query.

