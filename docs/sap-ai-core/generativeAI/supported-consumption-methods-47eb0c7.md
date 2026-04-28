<!-- loio47eb0c75cef546029aacd21c21cef447 -->

# Supported Consumption Methods

The following features are supported through SAP AI Core. Other features cited in the Azure Open AI documentation are not supported.

Ensure that you have the following headers set:


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



## Basic Text Generation

> ### Sample Code:  
> ```
> 
> curl --location conkeyref="$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "Count to 3 in Spanish."
> }'
> 
> 
> ```

> ### Output Code:  
> ```
> 
> {
>   "background": false,
>   "completed_at": 1775625426,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1152,
>         "start_offset": 1130
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "prompt"
>     },
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 480,
>         "start_offset": 0
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "completion"
>     }
>   ],
>   "created_at": 1775625423,
>   "error": null,
>   "frequency_penalty": 0.0,
>   "id": "resp_004fb524e4fff7f40069d5e4cfa8448195bf9627c7360e98a4",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_004fb524e4fff7f40069d5e4d045ec8195a5977f4fb6ed97c0",
>       "summary": [],
>       "type": "reasoning"
>     },
>     {
>       "content": [
>         {
>           "annotations": [],
>           "logprobs": [],
>           "text": "Uno, dos, tres.",
>           "type": "output_text"
>         }
>       ],
>       "id": "msg_004fb524e4fff7f40069d5e4d1b6bc8195b5d071ab98fbfdda",
>       "role": "assistant",
>       "status": "completed",
>       "type": "message"
>     }
>   ],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0.0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "completed",
>   "store": true,
>   "temperature": 1.0,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1.0,
>   "truncation": "disabled",
>   "usage": {
>     "input_tokens": 13,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 143,
>     "output_tokens_details": {
>       "reasoning_tokens": 128
>     },
>     "total_tokens": 156
>   },
>   "user": null
> }
> ```



## Stream Text Generation

> ### Sample Code:  
> ```
> 
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "Tell me a short joke.",
>   "stream": true
> }'
> ```

> ### Output Code:  
> ```
> 
> data: {"type":"response.created","response":{"id":"resp_0f2d32831fb00e2e0069d5f8e804808193b3379a80c7a3b172","object":"response","created_at":1775630568,"status":"in_progress","background":false,"completed_at":null,"content_filters":null,"error":null,"frequency_penalty":0.0,"incomplete_details":null,"instructions":null,"max_output_tokens":null,"max_tool_calls":null,"model":"gpt-5","output":[],"parallel_tool_calls":true,"presence_penalty":0.0,"previous_response_id":null,"prompt_cache_key":null,"prompt_cache_retention":null,"reasoning":{"effort":"medium","summary":null},"safety_identifier":null,"service_tier":"auto","store":true,"temperature":1.0,"text":{"format":{"type":"text"},"verbosity":"medium"},"tool_choice":"auto","tools":[],"top_logprobs":0,"top_p":1.0,"truncation":"disabled","usage":null,"user":null,"metadata":{}},"sequence_number":0}
> 
> data: {"type":"response.in_progress","response":{"id":"resp_0f2d32831fb00e2e0069d5f8e804808193b3379a80c7a3b172","object":"response","created_at":1775630568,"status":"in_progress","background":false,"completed_at":null,"content_filters":null,"error":null,"frequency_penalty":0.0,"incomplete_details":null,"instructions":null,"max_output_tokens":null,"max_tool_calls":null,"model":"gpt-5","output":[],"parallel_tool_calls":true,"presence_penalty":0.0,"previous_response_id":null,"prompt_cache_key":null,"prompt_cache_retention":null,"reasoning":{"effort":"medium","summary":null},"safety_identifier":null,"service_tier":"auto","store":true,"temperature":1.0,"text":{"format":{"type":"text"},"verbosity":"medium"},"tool_choice":"auto","tools":[],"top_logprobs":0,"top_p":1.0,"truncation":"disabled","usage":null,"user":null,"metadata":{}},"sequence_number":1}
> 
> data: {"type":"response.output_item.added","item":{"id":"rs_0f2d32831fb00e2e0069d5f8e8e4d4819388a333a13963c26c","type":"reasoning","summary":[]},"output_index":0,"sequence_number":2}
> 
> data: {"type":"response.output_item.done","item":{"id":"rs_0f2d32831fb00e2e0069d5f8e8e4d4819388a333a13963c26c","type":"reasoning","summary":[]},"output_index":0,"sequence_number":3}
> 
> data: {"type":"response.output_item.added","item":{"id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","type":"message","status":"in_progress","content":[],"role":"assistant"},"output_index":1,"sequence_number":4}
> 
> data: {"type":"response.content_part.added","content_index":0,"item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","output_index":1,"part":{"type":"output_text","annotations":[],"logprobs":[],"text":""},"sequence_number":5}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":"I","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"FLULWfR50RQt9xe","output_index":1,"sequence_number":6}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" made","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"Aqz8i3eh080","output_index":1,"sequence_number":7}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" a","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"gG89e4gtSwCR8X","output_index":1,"sequence_number":8}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" pencil","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"kuiQ2eTZo","output_index":1,"sequence_number":9}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" with","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"p6XFGSHfQYM","output_index":1,"sequence_number":10}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" two","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"VKPNZg4a8LVT","output_index":1,"sequence_number":11}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" er","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"hFwqXYfdYVgL6","output_index":1,"sequence_number":12}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":"asers","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"hJXekEK6KHi","output_index":1,"sequence_number":13}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":".","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"3AZgVGpzDEHyrh0","output_index":1,"sequence_number":14}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" It","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"SgobRaEGNbRJv","output_index":1,"sequence_number":15}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" was","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"NJXJX0CC6d4y","output_index":1,"sequence_number":16}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":" pointless","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"1c4UVp","output_index":1,"sequence_number":17}
> 
> data: {"type":"response.output_text.delta","content_index":0,"delta":".","item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"obfuscation":"nYlUlIwZ2i9vkBh","output_index":1,"sequence_number":18}
> 
> data: {"type":"response.output_text.done","content_index":0,"item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","logprobs":[],"output_index":1,"sequence_number":19,"text":"I made a pencil with two erasers. It was pointless."}
> 
> data: {"type":"response.content_part.done","content_index":0,"item_id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","output_index":1,"part":{"type":"output_text","annotations":[],"logprobs":[],"text":"I made a pencil with two erasers. It was pointless."},"sequence_number":20}
> 
> data: {"type":"response.output_item.done","item":{"id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","type":"message","status":"completed","content":[{"type":"output_text","annotations":[],"logprobs":[],"text":"I made a pencil with two erasers. It was pointless."}],"role":"assistant"},"output_index":1,"sequence_number":21}
> 
> data: {"type":"response.completed","response":{"id":"resp_0f2d32831fb00e2e0069d5f8e804808193b3379a80c7a3b172","object":"response","created_at":1775630568,"status":"completed","background":false,"completed_at":1775630571,"content_filters":[{"blocked":false,"source_type":"prompt","content_filter_raw":[],"content_filter_results":{"hate":{"filtered":false,"severity":"safe"},"self_harm":{"filtered":false,"severity":"safe"},"sexual":{"filtered":false,"severity":"safe"},"violence":{"filtered":false,"severity":"safe"}},"content_filter_offsets":{"start_offset":1130,"end_offset":1151,"check_offset":0}},{"blocked":false,"source_type":"completion","content_filter_raw":[],"content_filter_results":{"self_harm":{"filtered":false,"severity":"safe"},"sexual":{"filtered":false,"severity":"safe"},"violence":{"filtered":false,"severity":"safe"},"hate":{"filtered":false,"severity":"safe"}},"content_filter_offsets":{"start_offset":0,"end_offset":1163,"check_offset":0}}],"error":null,"frequency_penalty":0.0,"incomplete_details":null,"instructions":null,"max_output_tokens":null,"max_tool_calls":null,"model":"gpt-5","output":[{"id":"rs_0f2d32831fb00e2e0069d5f8e8e4d4819388a333a13963c26c","type":"reasoning","summary":[]},{"id":"msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6","type":"message","status":"completed","content":[{"type":"output_text","annotations":[],"logprobs":[],"text":"I made a pencil with two erasers. It was pointless."}],"role":"assistant"}],"parallel_tool_calls":true,"presence_penalty":0.0,"previous_response_id":null,"prompt_cache_key":null,"prompt_cache_retention":null,"reasoning":{"effort":"medium","summary":null},"safety_identifier":null,"service_tier":"auto","store":true,"temperature":1.0,"text":{"format":{"type":"text"},"verbosity":"medium"},"tool_choice":"auto","tools":[],"top_logprobs":0,"top_p":1.0,"truncation":"disabled","usage":{"input_tokens":12,"input_tokens_details":{"cached_tokens":0},"output_tokens":286,"output_tokens_details":{"reasoning_tokens":256},"total_tokens":298},"user":null,"metadata":{}},"sequence_number":22}
> 				
> ```



## Multi-turn Conversations

> ### Sample Code:  
> ```
> 
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "Count to 5 in Spanish."
> }'
> 
> ```

> ### Output Code:  
> ```
> 
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "What did I just ask you to count to?",
>   "previous_response_id": "resp_0c7d5a12cbe135ee0069d602027e98819785c54c92cbb2c33c"
> }'
> {
>   "background": false,
>   "completed_at": 1775632924,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1303,
>         "start_offset": 1267
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "prompt"
>     },
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 405,
>         "start_offset": 0
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "completion"
>     }
>   ],
>   "created_at": 1775632922,
>   "error": null,
>   "frequency_penalty": 0.0,
>   "id": "resp_0c7d5a12cbe135ee0069d6021a70048197b30eac95a9b0c028",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_0c7d5a12cbe135ee0069d6021ae4e08197aa623c16d9dd5c8f",
>       "summary": [],
>       "type": "reasoning"
>     },
>     {
>       "content": [
>         {
>           "annotations": [],
>           "logprobs": [],
>           "text": "5",
>           "type": "output_text"
>         }
>       ],
>       "id": "msg_0c7d5a12cbe135ee0069d6021cb13c8197a301edad5a9c0dca",
>       "role": "assistant",
>       "status": "completed",
>       "type": "message"
>     }
>   ],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0.0,
>   "previous_response_id": "resp_0c7d5a12cbe135ee0069d602027e98819785c54c92cbb2c33c",
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "completed",
>   "store": true,
>   "temperature": 1.0,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1.0,
>   "truncation": "disabled",
>   "usage": {
>     "input_tokens": 52,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 120,
>     "output_tokens_details": {
>       "reasoning_tokens": 64
>     },
>     "total_tokens": 172
>   },
>   "user": null
> }
> ```



## Tool Calling

> ### Sample Code:  
> ```
> 
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "What is the weather in Berlin today?",
>   "tools": [
>     {
>       "type": "function",
>       "name": "get_weather",
>       "description": "Retrieves current weather for a given location.",
>       "parameters": {
>         "type": "object",
>         "properties": {
>           "location": {
>             "type": "string",
>             "description": "City name, e.g. Berlin"
>           },
>           "unit": {
>             "type": "string",
>             "enum": ["celsius", "fahrenheit"],
>             "description": "Temperature unit"
>           }
>         },
>         "required": ["location"]
>       }
>     }
>   ],
>   "tool_choice": "auto"
> }'
> 
> 
> ```

> ### Output Code:  
> ```
> 
> {
>   "background": false,
>   "completed_at": 1775633033,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 66,
>         "start_offset": 30
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "prompt"
>     },
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1964,
>         "start_offset": 0
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "completion"
>     }
>   ],
>   "created_at": 1775633030,
>   "error": null,
>   "frequency_penalty": 0,
>   "id": "resp_047ee244b82be67b0069d60285fbf881968ffc2e359a601595",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_047ee244b82be67b0069d60286a7e48196bf5d878ac3101a4d",
>       "summary": [],
>       "type": "reasoning"
>     },
>     {
>       "arguments": "{\"location\":\"Berlin\",\"unit\":\"celsius\"}",
>       "call_id": "call_pcSA7YDBUkKraA3gPYC6BoCx",
>       "id": "fc_047ee244b82be67b0069d60288a4e88196a01c79cb1955ce19",
>       "name": "get_weather",
>       "status": "completed",
>       "type": "function_call"
>     }
>   ],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "completed",
>   "store": true,
>   "temperature": 1,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [
>     {
>       "description": "Retrieves current weather for a given location.",
>       "name": "get_weather",
>       "parameters": {
>         "additionalProperties": false,
>         "properties": {
>           "location": {
>             "description": "City name, e.g. Berlin",
>             "type": "string"
>           },
>           "unit": {
>             "description": "Temperature unit",
>             "enum": [
>               "celsius",
>               "fahrenheit"
>             ],
>             "type": "string"
>           }
>         },
>         "required": [
>           "location",
>           "unit"
>         ],
>         "type": "object"
>       },
>       "strict": true,
>       "type": "function"
>     }
>   ],
>   "top_logprobs": 0,
>   "top_p": 1,
>   "truncation": "disabled",
>   "usage": {
>     "input_tokens": 78,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 175,
>     "output_tokens_details": {
>       "reasoning_tokens": 128
>     },
>     "total_tokens": 253
>   },
>   "user": null
> }
> ```



## Tuning Reasoning Effort

> ### Sample Code:  
> ```
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "Solve: If a train travels 120 km in 1.5 hours, what is its average speed?",
>   "reasoning": {
>     "effort": "high",
>     "summary": "concise"
>   }
> }'
> 
> ```

> ### Output Code:  
> ```
> 
> {
>   "background": false,
>   "completed_at": 1775635760,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1204,
>         "start_offset": 1131
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "prompt"
>     },
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 464,
>         "start_offset": 0
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "completion"
>     }
>   ],
>   "created_at": 1775635752,
>   "error": null,
>   "frequency_penalty": 0.0,
>   "id": "resp_0fd09a736f9430c10069d60d28e08c8196b8a4960041311c66",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_0fd09a736f9430c10069d60d299a908196bb8d9631ee09094e",
>       "summary": [
>         {
>           "text": "**Calculating average speed**\n\nI need to solve for average speed using the formula: speed = distance/time. For 120 km over 1.5 hours, I find the speed is 80 km/h. Checking the math: 120 divided by 1.5 gives 80 too. The explanation is straightforward: average speed equals distance divided by time, so that's 120 km divided by 1.5 hours. I could also express it in meters per second, but I'll keep it simple, as the user didn't request that.",
>           "type": "summary_text"
>         }
>       ],
>       "type": "reasoning"
>     },
>     {
>       "content": [
>         {
>           "annotations": [],
>           "logprobs": [],
>           "text": "Average speed = distance ÷ time = 120 km ÷ 1.5 h = 80 km/h.",
>           "type": "output_text"
>         }
>       ],
>       "id": "msg_0fd09a736f9430c10069d60d301c588196ae389bfac11f1621",
>       "role": "assistant",
>       "status": "completed",
>       "type": "message"
>     }
>   ],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0.0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "high",
>     "summary": "concise"
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "completed",
>   "store": true,
>   "temperature": 1.0,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1.0,
>   "truncation": "disabled",
>   "usage": {
>     "input_tokens": 28,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 162,
>     "output_tokens_details": {
>       "reasoning_tokens": 128
>     },
>     "total_tokens": 190
>   },
>   "user": null
> }
> ```



## Structured Output

Use `text.format` to constrain the model's output to a JSON schema. Set `strict:` *<true\>* to enforce exact schema compliance

> ### Sample Code:  
> ```
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "Extract the name and age from: John is 30 years old.",
>   "text": {
>     "format": {
>       "type": "json_schema",
>       "name": "person",
>       "strict": true,
>       "schema": {
>         "type": "object",
>         "properties": {
>           "name": { "type": "string" },
>           "age":  { "type": "integer" }
>         },
>         "required": ["name", "age"],
>         "additionalProperties": false
>       }
>     }
>   }
> }'
> 
> 
> ```

> ### Output Code:  
> ```
> 
> {
>   "background": false,
>   "completed_at": 1775660677,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1321,
>         "start_offset": 1269
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "prompt"
>     },
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1533,
>         "start_offset": 0
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "completion"
>     }
>   ],
>   "created_at": 1775660669,
>   "error": null,
>   "frequency_penalty": 0.0,
>   "id": "resp_0261fdc22b6a21c50069d66e7d76ec8194bcf4bad9e6697593",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_0261fdc22b6a21c50069d66e7e05c08194b3f66d0adb40909d",
>       "summary": [],
>       "type": "reasoning"
>     },
>     {
>       "content": [
>         {
>           "annotations": [],
>           "logprobs": [],
>           "text": "{\"name\":\"John\",\"age\":30}",
>           "type": "output_text"
>         }
>       ],
>       "id": "msg_0261fdc22b6a21c50069d66e8581b881948631e41a40256fa8",
>       "role": "assistant",
>       "status": "completed",
>       "type": "message"
>     }
>   ],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0.0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "completed",
>   "store": true,
>   "temperature": 1.0,
>   "text": {
>     "format": {
>       "description": null,
>       "name": "person",
>       "schema": {
>         "additionalProperties": false,
>         "properties": {
>           "age": {
>             "type": "integer"
>           },
>           "name": {
>             "type": "string"
>           }
>         },
>         "required": [
>           "name",
>           "age"
>         ],
>         "type": "object"
>       },
>       "strict": true,
>       "type": "json_schema"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1.0,
>   "truncation": "disabled",
>   "usage": {
>     "input_tokens": 48,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 354,
>     "output_tokens_details": {
>       "reasoning_tokens": 320
>     },
>     "total_tokens": 402
>   },
>   "user": null
> }
> ```



## Background Mode

Set `background:` *<true\>* to run a long-running response asynchronously. Poll `GET /responses/{id}` to check status, or cancel with `POST /responses/{id}/cancel`.

> ### Sample Code:  
> ```
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "Write a 1 page report on AI trends.",
>   "background": true
> }'
> 
> 
> ```
> 
> ```
> 
> {
>   "background": true,
>   "completed_at": null,
>   "content_filters": null,
>   "created_at": 1775660765,
>   "error": null,
>   "frequency_penalty": 0.0,
>   "id": "resp_00a26cdc24b0dd070069d66edd127c819598a74a3355ed43b4",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0.0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "queued",
>   "store": true,
>   "temperature": 1.0,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1.0,
>   "truncation": "disabled",
>   "usage": null,
>   "user": null
> }
> 
> 
> ```

> ### Output Code:  
> ```
> 
> curl "$DEPLOYMENT_URL/responses/<response_id>" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header "Authorization: Bearer $AUTH_TOKEN"
> 
> 
> ```
> 
> ```
> 
> {
>   "background": true,
>   "completed_at": null,
>   "content_filters": null,
>   "created_at": 1775660765,
>   "error": {
>     "code": "server_error",
>     "message": "An error occurred while processing your request. You can retry your request, or contact us through an Azure support request at: https://go.microsoft.com/fwlink/?linkid=2213926 if the error persists. Please include the request ID wfr_019d6da1103b753ca4c0e3ed0bd8c380 in your message."
>   },
>   "frequency_penalty": 0.0,
>   "id": "resp_00a26cdc24b0dd070069d66edd127c819598a74a3355ed43b4",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0.0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "failed",
>   "store": true,
>   "temperature": 1.0,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1.0,
>   "truncation": "disabled",
>   "usage": null,
>   "user": null
> }
> 
> 
> ```
> 
> ```
> 
> {
>   "background": true,
>   "completed_at": null,
>   "content_filters": null,
>   "created_at": 1775661040,
>   "error": null,
>   "frequency_penalty": 0,
>   "id": "resp_00e6f5f17ced9f150069d66ff06ae88190b59be9ab2616d9d3",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "in_progress",
>   "store": true,
>   "temperature": 1,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1,
>   "truncation": "disabled",
>   "usage": null,
>   "user": null
> }
> 
> 
> ```
> 
> ```
> 
> {
>   "background": true,
>   "completed_at": 1775661083,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1165,
>         "start_offset": 1130
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "prompt"
>     },
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 8975,
>         "start_offset": 0
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "completion"
>     }
>   ],
>   "created_at": 1775661040,
>   "error": null,
>   "frequency_penalty": 0.0,
>   "id": "resp_00e6f5f17ced9f150069d66ff06ae88190b59be9ab2616d9d3",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_00e6f5f17ced9f150069d66ff199d08190a7b6ac8fe41f3e78",
>       "summary": [],
>       "type": "reasoning"
>     },
>     {
>       "content": [
>         {
>           "annotations": [],
>           "logprobs": [],
>           "text": "AI Trends: A Brief Report\n\nSummary\nArtificial intelligence is shifting from single-task models to integrated systems that plan, call tools, and operate across text, images, audio, and video. Organizations are moving from pilots to production, emphasizing reliability, governance, and cost control. The focus is no longer just “bigger models,” but right-sizing, data quality, and system design that blends models with retrieval, tools, and human oversight.\n\nKey Trends\n\n- From copilots to agents\n  - Evolution from assistive “copilots” to agentic systems that break tasks into steps, call APIs, browse, write code, and act.\n  - Tool use (function calling), planning, and memory are becoming standard features, often orchestrated by workflow engines.\n  - Emphasis on guardrails, deterministic steps for critical actions, and human-in-the-loop checkpoints.\n\n- Multimodal AI becomes default\n  - Models that understand and generate across text, images, audio, and video are increasingly practical.\n  - Use cases: knowledge search with charts and images, call-center QA on transcripts, inspection and defect detection, meeting summaries with slide context, and video analytics.\n  - OCR and table understanding are integrated into general-purpose models, reducing bespoke pipelines.\n\n- Smaller, specialized models rise\n  - “Small language models” (SLMs) and distilled variants deliver adequate performance at a fraction of cost and latency.\n  - Domain-tuned and instruction-tuned models outperform larger general models on narrow tasks.\n  - On-device and edge inference grows for privacy, latency, and offline use.\n\n- Data and retrieval over sheer parameter count\n  - Retrieval-augmented generation (RAG) is standard: grounding answers in structured and unstructured corpora to cut hallucinations.\n  - Trend toward RAG 2.0: better chunking, hybrid search (sparse + dense), graph-augmented retrieval, and citations with confidence.\n  - Synthetic data generation is common for rare cases and preference tuning, raising governance needs for provenance and bias control.\n\n- Training and alignment advances\n  - Shift from RLHF alone to a mix of methods: direct preference optimization (DPO), reinforcement learning from AI feedback (RLAIF), and iterative self-play for tools and code.\n  - Preference modeling increasingly task- and org-specific; model behavior shaped by policy libraries and domain rules.\n\n- Inference efficiency and architectures\n  - Mixture-of-experts (MoE), speculative decoding, and KV-cache management reduce latency and cost.\n  - Quantization and low-rank adaptation (LoRA) enable on-prem/edge deployments.\n  - Throughput, context length, and structured output reliability matter more than headline benchmarks.\n\n- Reliability, evaluation, and verifiability\n  - Production teams treat LLM systems like software: test suites, adversarial evaluation, and continuous monitoring for drift.\n  - Techniques to reduce hallucinations: retrieval-first prompting, constrained decoding, citations, programmatic checks, and self-consistency voting.\n  - Model claims are increasingly tied to evidence: provenance metadata, watermarking/signatures for generated media, and audit trails.\n\n- Security and privacy\n  - Prompt injection, data exfiltration, model poisoning, and jailbreaks are now standard threat models.\n  - Countermeasures: input/output filters, tool permissioning, sandboxing, rate limits, and red-teaming.\n  - Federated learning and differential privacy remain relevant where regulated data is involved.\n\n- Governance and regulation\n  - Organizations align with emerging frameworks (e.g., NIST AI RMF) and sector-specific rules.\n  - System cards, model cards, incident response plans, and vendor risk assessments are becoming procurement staples.\n  - Documentation, consent, and IP considerations for training and outputs are front-and-center.\n\n- Open vs. proprietary ecosystems\n  - Open models improve rapidly, enabling customization and offline use; licensing and safety vary.\n  - Proprietary frontier models still lead on complex reasoning and multimodal fidelity, especially at long context.\n  - Many stacks adopt a hybrid: open models for routine tasks, proprietary for high-stakes or complex reasoning.\n\nImplications for Organizations\n\n- Start with the system, not the model: combine retrieval, tools, and guardrails; measure end-to-end outcomes.\n- Optimize for total cost of ownership: choose the smallest model that meets quality; exploit quantization and caching.\n- Invest in data pipelines: document quality, build feedback loops, and track provenance for both real and synthetic data.\n- Treat safety and security as engineering disciplines: red-team, monitor, and restrict tool permissions.\n- Plan for change: abstract model providers behind interfaces; keep prompts, tools, and evaluations portable.\n\nKey Metrics to Track\n\n- Quality: task-specific pass rates, grounded citation rate, factuality and consistency.\n- Cost/latency: cost per 1K/1M tokens, tokens/sec, P95/P99 latency.\n- Reliability: hallucination rate, tool-call accuracy, eval drift over time.\n- Adoption: task coverage, time-to-completion, user satisfaction, and ROI.",
>           "type": "output_text"
>         }
>       ],
>       "id": "msg_00e6f5f17ced9f150069d6700505e481909b3f2c01fc4e5411",
>       "role": "assistant",
>       "status": "completed",
>       "type": "message"
>     }
>   ],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0.0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "completed",
>   "store": true,
>   "temperature": 1.0,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1.0,
>   "truncation": "disabled",
>   "usage": {
>     "input_tokens": 16,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 1946,
>     "output_tokens_details": {
>       "reasoning_tokens": 896
>     },
>     "total_tokens": 1962
>   },
>   "user": null
> }
> ```



## Stateless \(store: false\)

Set `store:` *<false\>* to prevent the response from being stored server-side. Pass the full conversation history in `input` on each turn. Use include:`["reasoning.encrypted_content"]`to carry reasoning tokens across turns.

> ### Sample Code:  
> ```
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "store": false,
>   "input": [
>     { "role": "user",      "content": "Count to 3 in Spanish." },
>     { "role": "assistant", "content": "Uno, dos, tres." },
>     { "role": "user",      "content": "Now count to 5." }
>   ]
> }'
> 
> 
> ```

> ### Output Code:  
> ```
> 
> {
>   "background": false,
>   "completed_at": 1775661288,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1253,
>         "start_offset": 1238
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "prompt"
>     },
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 732,
>         "start_offset": 0
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "completion"
>     }
>   ],
>   "created_at": 1775661284,
>   "error": null,
>   "frequency_penalty": 0,
>   "id": "resp_083ce1293c8376680169d670e4bec481968f1ed8a8e235e7c2",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_083ce1293c8376680169d670e57b548196b9d623b0def49a52",
>       "summary": [],
>       "type": "reasoning"
>     },
>     {
>       "content": [
>         {
>           "annotations": [],
>           "logprobs": [],
>           "text": "Uno, dos, tres, cuatro, cinco.",
>           "type": "output_text"
>         }
>       ],
>       "id": "msg_083ce1293c8376680169d670e7cb7c81969f7f0e7c85cc0433",
>       "role": "assistant",
>       "status": "completed",
>       "type": "message"
>     }
>   ],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0,
>   "previous_response_id": null,
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "completed",
>   "store": false,
>   "temperature": 1,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1,
>   "truncation": "disabled",
>   "usage": {
>     "input_tokens": 35,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 185,
>     "output_tokens_details": {
>       "reasoning_tokens": 128
>     },
>     "total_tokens": 220
>   },
>   "user": null
> }
> ```



## Truncation

Set `truncation:` `"auto"` to automatically drop the oldest messages when the conversation exceeds the model's context limit. The default`"disabled"` returns an error instead.

> ### Sample Code:  
> ```
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "Summarize our conversation so far.",
>   "previous_response_id": "resp_00e6f5f17ced9f150069d66ff06ae88190b59be9ab2616d9d3",
>   "truncation": "auto"
> }'
> 
> 
> ```

> ### Output Code:  
> ```
> 
> {
>   "background": false,
>   "completed_at": 1775661392,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 6493,
>         "start_offset": 6459
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "prompt"
>     },
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 3224,
>         "start_offset": 0
>       },
>       "content_filter_raw": [],
>       "content_filter_results": {
>         "hate": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "self_harm": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "sexual": {
>           "filtered": false,
>           "severity": "safe"
>         },
>         "violence": {
>           "filtered": false,
>           "severity": "safe"
>         }
>       },
>       "source_type": "completion"
>     }
>   ],
>   "created_at": 1775661382,
>   "error": null,
>   "frequency_penalty": 0.0,
>   "id": "resp_00e6f5f17ced9f150069d6714554908190b834ab02e37bd4ab",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_00e6f5f17ced9f150069d67146af848190801dd7eca493f431",
>       "summary": [],
>       "type": "reasoning"
>     },
>     {
>       "content": [
>         {
>           "annotations": [],
>           "logprobs": [],
>           "text": "Here’s a brief recap:\n\n- You asked for a 1-page report on AI trends.\n- I provided a report highlighting:\n  - Shift from copilots to agentic systems with tool use, planning, and guardrails.\n  - Multimodal AI (text, image, audio, video) becoming standard.\n  - Rise of smaller/specialized and on-device models for cost, latency, and privacy.\n  - Emphasis on data quality and retrieval (RAG), including advanced retrieval techniques.\n  - Training/alignment advances (e.g., DPO, RLAIF) and domain-specific preference modeling.\n  - Inference efficiency (MoE, speculative decoding, KV-cache, quantization, LoRA) and focus on throughput/context.\n  - Reliability and verifiability via testing, citations, constrained decoding, and monitoring.\n  - Security/privacy threats and mitigations; red-teaming and sandboxing.\n  - Governance/regulation practices and hybrid open/proprietary model strategies.\n- Practical guidance included system-first design, TCO optimization, strong data pipelines, safety/security as engineering, and provider abstraction.\n- Suggested metrics: quality, cost/latency, reliability, and adoption/ROI.",
>           "type": "output_text"
>         }
>       ],
>       "id": "msg_00e6f5f17ced9f150069d6714c8d908190ac535907666545f7",
>       "role": "assistant",
>       "status": "completed",
>       "type": "message"
>     }
>   ],
>   "parallel_tool_calls": true,
>   "presence_penalty": 0.0,
>   "previous_response_id": "resp_00e6f5f17ced9f150069d66ff06ae88190b59be9ab2616d9d3",
>   "prompt_cache_key": null,
>   "prompt_cache_retention": null,
>   "reasoning": {
>     "effort": "medium",
>     "summary": null
>   },
>   "safety_identifier": null,
>   "service_tier": "auto",
>   "status": "completed",
>   "store": true,
>   "temperature": 1.0,
>   "text": {
>     "format": {
>       "type": "text"
>     },
>     "verbosity": "medium"
>   },
>   "tool_choice": "auto",
>   "tools": [],
>   "top_logprobs": 0,
>   "top_p": 1.0,
>   "truncation": "auto",
>   "usage": {
>     "input_tokens": 1065,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 692,
>     "output_tokens_details": {
>       "reasoning_tokens": 384
>     },
>     "total_tokens": 1757
>   },
>   "user": null
> }
> ```



## Prompt Caching

Use `prompt_cache_key`to group similar requests and maximize cache reuse. Set prompt\_cache\_retention to control how long the cache entry is kept.

> ### Sample Code:  
> ```
> curl --location "$DEPLOYMENT_URL/responses" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>   "model": "gpt-5",
>   "input": "What is the capital of France?",
>   "prompt_cache_key": "user_session_abc123"
> }'
> 
> ```

> ### Output Code:  
> ```
> 
> {
>   "id": "resp_cache123",
>   "object": "response",
>   "status": "completed",
>   "model": "gpt-5",
>   "prompt_cache_key": "user_session_abc123",
>   "prompt_cache_retention": "24h",
>   "output": [
>     {
>       "type": "message",
>       "role": "assistant",
>       "content": [
>         {
>           "type": "output_text",
>           "text": "The capital of France is Paris."
>         }
>       ]
>     }
>   ],
>   "usage": {
>     "input_tokens": 10,
>     "input_tokens_details": {
>       "cached_tokens": 8
>     },
>     "output_tokens": 9,
>     "output_tokens_details": {
>       "reasoning_tokens": 0
>     },
>     "total_tokens": 19
>   }
> }
> ```

