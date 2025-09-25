<!-- loio2e478712a9794bc1b0a6f95f60060fc7 -->

# Tool Calling

You can incorporate specialist tools into your orchestration workflow for example to make an API call for current data or to execute custom code. LLMs decide that a tool call is needed based on your system prompt, messages and tool definition. You then execute your function code, return the results and the model will incorporate the results into its response.

You can define multiple tools, and use the decision making capabilities of generative AI models to guide you in their use.



<a name="loio2e478712a9794bc1b0a6f95f60060fc7__section_vc2_1nx_ffc"/>

## Example

The following code shows a tool containing a custom function for an API call to retrieve item quantity information from an inventory:

> ### Sample Code:  
> ```
> import requests
> 
> def get_inventory_quantity(product_id):
> 	response = requests.get(f"https://my-store-api.com/v1/inventory?product_id={product_id}")
> 	data = response.json()
> 	return data['product_id']['quantity']
> ```

You can include tools in your template by providing and outline of the function and its arguments in your template. You can include guidance on when a tool should be used in your system messages.

The following call includes an outline of the get\_inventory\_quantity function above in the `tools` parameter, with a description of its use case in the system role content. The `placeholder_values` include a request for product ID 123456.

> ### Sample Code:  
> ```
> curl --request POST \
>   --url {{orchestration_deployment_url}}/v2/completion \
>   --header 'AI-Resource-Group: default' \
>   --header 'Authorization: Bearer {{token}}' \
>   --header 'content-type: application/json' \
>   --data '{
>   "config": {
>     "modules": {
>       "prompt_templating": {
>         "prompt": {
>           "template": [
>           {
>             "role": "system",
>             "content": "You are a helpful assistant. You help users to analyze inventory of the user's store by calling the get_inventory_quantity function."
>           },
>           {
>             "role": "user",
>             "content": "How many units of the product with ID {{ ?product_id }} are in stock?"
>           }
>         ],
>         "tools": [
>           {
>             "type": "function",
>             "function": {
>               "name": "get_inventory_quantity",
>               "description": "Check available quantity for a product ID.",
>               "strict": true,
>               "parameters": {
>                 "type": "object",
>                 "properties": {
>                   "product_id": {
>                     "type": "integer"
>                   }
>                 },
>                 "required": [
>                   "product_id"
>                 ],
>                 "additionalProperties": false
>               }
>             }
>           }
>         ]
>         },
>         "model": {
>           "name": "gpt-4o",
>           "params": {
>             "max_tokens": 200
>           }
>         }
>       }
>     }
>   },
>   "placeholder_values": {
>     "product_id": "123456"
>   }
> }'
> ```

The model uses the tool definition to decide that a function call is needed, and returns the function name and its input arguments in the format defined in the template. Use the information provided to call your custom function.

> ### Output Code:  
> ```
> {
>   "request_id": "c3a3aeb5-5044-9152-8c3b-cf2fa4c07b25",
>   "intermediate_results": {
>     "templating": [
>       {
>         "role": "system",
>         "content": "You are a helpful assistant. You help users to analyze inventory of the user's store by calling the get_inventory_quantity function."
>       },
>       {
>         "content": "How many units of the product with ID 123456 are in stock?",
>         "role": "user"
>       }
>     ],
>     "llm": {
>       "id": "chatcmpl-BuZqH3BWFuVVuge7Hg73ecLutnTje",
>       "object": "chat.completion",
>       "created": 1752823845,
>       "model": "gpt-4o-2024-08-06",
>       "system_fingerprint": "fp_ee1d74bde0",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "",
>             "tool_calls": [
>               {
>                 "id": "call_9yP43Z8VwoEQoB8mCdfsUQ3b",
>                 "type": "function",
>                 "function": {
>                   "name": "get_inventory_quantity",
>                   "arguments": "{\"product_id\":123456}"
>                 }
>               }
>             ]
>           },
>           "finish_reason": "tool_calls"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 18,
>         "prompt_tokens": 86,
>         "total_tokens": 104
>       }
>     }
>   },
>   "final_result": {
>     "id": "chatcmpl-BuZqH3BWFuVVuge7Hg73ecLutnTje",
>     "object": "chat.completion",
>     "created": 1752823845,
>     "model": "gpt-4o-2024-08-06",
>     "system_fingerprint": "fp_ee1d74bde0",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "",
>           "tool_calls": [
>             {
>               "id": "call_9yP43Z8VwoEQoB8mCdfsUQ3b",
>               "type": "function",
>               "function": {
>                 "name": "get_inventory_quantity",
>                 "arguments": "{\"product_id\":123456}"
>               }
>             }
>           ]
>         },
>         "finish_reason": "tool_calls"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 18,
>       "prompt_tokens": 86,
>       "total_tokens": 104
>     }
>   }
> }
> ```

When you have called your custom function, use the response to extend your LLM call.

In the following example, the function call has returned a quantity of 25 items in integer format. This information is inserted into the `template` in the `tool` role.

> ### Sample Code:  
> ```
> curl --request POST \
>   --url {{orchestration_deployment_url}}/v2/completion \
>   --header 'AI-Resource-Group: default' \
>   --header 'Authorization: Bearer {{token}}' \
>   --header 'content-type: application/json' \
>   --data '{
>   "config": {
>     "modules": {
>       "prompt_templating": {
>         "prompt": {
>           "template": [
>           {
>             "role": "system",
>             "content": "You are a helpful assistant. You help users to analyze inventory of the user'\''s store by calling the get_inventory_quantity function."
>           },
>           {
>             "role": "user",
>             "content": "How many units of the product with ID {{ ?product_id }} are in stock?"
>           },
>           # append the function call message
>           {
>             "role": "assistant",
>             "content": "",
>             "tool_calls": [
>               {
>                 "id": "call_il3KDaSC5zm6naTOnYv5VSZT",
>                 "type": "function",
>                 "function": {
>                   "name": "get_inventory_quantity",
>                   "arguments": "{\"product_id\":123456}"
>                 }
>               }
>             ]
>           },
>           # append function result
>           {
>             "role": "tool",
>             "tool_call_id": "call_il3KDaSC5zm6naTOnYv5VSZT",
>             "content": "25"
>           }
>         ],
>         "tools": [
>           {
>             "type": "function",
>             "function": {
>               "name": "get_inventory_quantity",
>               "description": "Check available quantity for a product ID.",
>               "strict": true,
>               "parameters": {
>                 "type": "object",
>                 "properties": {
>                   "product_id": {
>                     "type": "integer"
>                   }
>                 },
>                 "required": [
>                   "product_id"
>                 ],
>                 "additionalProperties": false
>               }
>             }
>           }
>         ]
>         },
>         "model": {
>           "name": "gpt-4o",
>           "params": {
>             "max_tokens": 200
>           }
>         }
>       }
>     }
>   },
>   "placeholder_values": {
>     "product_id": "123456"
>   }
> }'
> ```

The model answers the query, incorporating the result of the function call into its response:

> ### Output Code:  
> ```
> {
>   "request_id": "9b34a47b-14f1-95d3-9f84-51bdc4d66c2d",
>   "intermediate_results": {
>     "templating": [
>       {
>         "role": "system",
>         "content": "You are a helpful assistant. You help users to analyze inventory of the users store by calling the get_inventory_quantity function."
>       },
>       {
>         "content": "How many units of the product with ID 123456 are in stock?",
>         "role": "user"
>       },
>       {
>         "role": "assistant",
>         "content": "",
>         "tool_calls": [
>           {
>             "id": "call_il3KDaSC5zm6naTOnYv5VSZT",
>             "type": "function",
>             "function": {
>               "name": "get_inventory_quantity",
>               "arguments": "{\"product_id\":123456}"
>             }
>           }
>         ]
>       },
>       {
>         "role": "tool",
>         "tool_call_id": "call_il3KDaSC5zm6naTOnYv5VSZT",
>         "content": "25"
>       }
>     ],
>     "llm": {
>       "id": "chatcmpl-BuZvTwr6ZSxebgqHn8vp46zntVcZ1",
>       "object": "chat.completion",
>       "created": 1752824167,
>       "model": "gpt-4o-2024-08-06",
>       "system_fingerprint": "fp_ee1d74bde0",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "There are 25 units of the product with ID 123456 in stock."
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 18,
>         "prompt_tokens": 113,
>         "total_tokens": 131
>       }
>     }
>   },
>   "final_result": {
>     "id": "chatcmpl-BuZvTwr6ZSxebgqHn8vp46zntVcZ1",
>     "object": "chat.completion",
>     "created": 1752824167,
>     "model": "gpt-4o-2024-08-06",
>     "system_fingerprint": "fp_ee1d74bde0",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "There are 25 units of the product with ID 123456 in stock."
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 18,
>       "prompt_tokens": 113,
>       "total_tokens": 131
>     }
>   }
> }
> ```

