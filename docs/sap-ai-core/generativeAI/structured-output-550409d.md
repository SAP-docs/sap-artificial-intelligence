<!-- loio550409de3da34f7884be964b9c8d33db -->

# Structured Output

You can use structured outputs to ensure that model generated outputs match schemas that you define.

Structured outputs exist in the following forms:

-   Function calling, such as for tool usage

    Function calling is helpful for agentic use cases where the LLM determines which tool to use out of a provided selection of tools. The LLM determines which tool is best for the use case, but the tool needs to be called separately in the application.

    > ### Sample Code:  
    > ```
    > "templating_module_config": {
    >     "template": [
    >         {
    >             "role": "system",
    >             "content": "You are a helpful assistant. You help users do math by calling the abs function."
    >         },
    >         {
    >             "role": "user",
    >             "content": "Whats the absolute value of 3?"
    >         }
    >     ],
    >     "tools": [
    >         {
    >             "type": "function",
    >             "function": {
    >                 "name": "abs",
    >                 "description": "Calculate the absolute value of x.",
    >                 "strict": true,
    >                 "parameters": {
    >                     "type": "object",
    >                     "properties": {
    >                         "x": {
    >                             "type": "integer"
    >                         }
    >                     },
    >                     "required": [
    >                         "x"
    >                     ],
    >                     "additionalProperties": false
    >                 }
    >             }
    >         }
    >     ]
    > }
    > 
    > ```

-   JSON response format

    JSON formats can be consumed in an application

    ```
      "templating_module_config": {
            "template": [
                {
                    "role": "system",
                    "content": "You are a language translator."
                },
                {
                    "role": "user",
                    "content": "Whats 'Apple' in German?"
                }
            ],
            "response_format": {
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
        }
    
    ```


Orchestration harmonizes tool usage and JSON response format across different models. For more information on which models support these features, see the documentation from the respective model provider.

For more information on structured outputs, see [Open AI Structured Outputs](https://openai.com/index/introducing-structured-outputs-in-the-api/) and [Open AI Structured Output Guide](https://platform.openai.com/docs/guides/structured-outputs).

