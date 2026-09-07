<!-- loio9be70e1dcad54200bc7ab1a6479aa96f -->

# Response Format

You can format responses to ensure that model generated outputs match schemas that you define. This is helpful, for example, with tool calling where you want the output to be consumed later without friction.

For more information, see [Structured Outpus in SAP AI Core](https://help.sap.com/docs/AI_CORE/b9f48eb4a993445b863a55dd4d38f64d/550409de3da34f7884be964b9c8d33db.html).

**Example**

```
{
  "type": "json_schema",
  "json_schema": {
    "name": "translation_response",
    "strict": true,
    "schema": {
      "type": "object",
      "properties": {
        "language": {
          "type": "string"
        },
        "translation": {
          "type": "string"
        }
      },
      "required": [
        "language",
        "translation"
      ],
      "additionalProperties": false
    }
  }
}
```

