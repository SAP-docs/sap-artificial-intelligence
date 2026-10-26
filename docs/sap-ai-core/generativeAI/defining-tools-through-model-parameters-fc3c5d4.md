<!-- loiofc3c5d414bd74564bff0dd9244fb981a -->

# Defining Tools through Model Parameters

In addition to defining tools in the template's `tools` array, you can define tools in `model.params.tools`. This approach is useful when the tool list is assembled dynamically at runtime instead of being stored in a template.

The tools defined in `model.params.tools` are included as part of the model configuration and are available during request processing.

```
{
  "model": {
    "name": "gpt-4o",
    "params": {
      "tools": [
        {
          "type": "function",
          "function": {
            "name": "get_inventory_quantity",
            "description": "Check available quantity for a product ID.",
            "parameters": {
              "type": "object",
              "properties": {
                "product_id": {
                  "type": "integer"
                }
              },
              "required": [
                "product_id"
              ]
            }
          }
        }
      ],
      "tool_choice": "auto"
    }
  }
}
```



## Tool Precedence

When `model.params.tools` is specified, it takes precedence over any tools defined in the template.

Orchestration does not merge tools from the template and `model.params.tools`. Template-defined tools are used only when the `model.params` object does not contain a `tools` key.

> ### Note:  
> When you use `model.params.tools`, specify additional tool-related parameters, such as `tool_choice` and `parallel_tool_calls`, in the `model.params` object.

