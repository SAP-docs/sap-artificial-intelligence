<!-- loio72fb07e8ead444f79e6ad6a89f328298 -->

# Lifecycle Management

Manages the lifecycle of a response created using the OpenAI Responses API. It allows you to retrieve a response by ID, cancel an in-progress response, or permanently delete a response for cleanup and control purposes.

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



## Retrieve a Response by Id

> ### Sample Code:  
> ```
> curl "$DEPLOYMENT_URL/responses/<response_id> \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header "Authorization: Bearer $AUTH_TOKEN"
> 
> ```

> ### Output Code:  
> ```
> {
>   "background": false,
>   "completed_at": 1775630571,
>   "content_filters": [
>     {
>       "blocked": false,
>       "content_filter_offsets": {
>         "check_offset": 0,
>         "end_offset": 1151,
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
>         "end_offset": 1163,
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
>   "created_at": 1775630568,
>   "error": null,
>   "frequency_penalty": 0.0,
>   "id": "resp_0f2d32831fb00e2e0069d5f8e804808193b3379a80c7a3b172",
>   "incomplete_details": null,
>   "instructions": null,
>   "max_output_tokens": null,
>   "max_tool_calls": null,
>   "metadata": {},
>   "model": "gpt-5",
>   "object": "response",
>   "output": [
>     {
>       "id": "rs_0f2d32831fb00e2e0069d5f8e8e4d4819388a333a13963c26c",
>       "summary": [],
>       "type": "reasoning"
>     },
>     {
>       "content": [
>         {
>           "annotations": [],
>           "logprobs": [],
>           "text": "I made a pencil with two erasers. It was pointless.",
>           "type": "output_text"
>         }
>       ],
>       "id": "msg_0f2d32831fb00e2e0069d5f8eb771081939ac98a1af19dbfa6",
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
>     "input_tokens": 12,
>     "input_tokens_details": {
>       "cached_tokens": 0
>     },
>     "output_tokens": 286,
>     "output_tokens_details": {
>       "reasoning_tokens": 256
>     },
>     "total_tokens": 298
>   },
>   "user": null
> }
> ```



## Cancel a Response by Id

> ### Sample Code:  
> ```
> curl --request POST --location "$DEPLOYMENT_URL/responses/<response_id>/cancel" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header "Authorization: Bearer $AUTH_TOKEN"
> ```

> ### Output Code:  
> ```
> {
>   "error": {
>     "code": null,
>     "message": "Cannot cancel a synchronous response.",
>     "param": null,
>     "type": "invalid_request_error"
>   }
> }
> ```



## Delete a Response by Id

> ### Sample Code:  
> ```
> curl --request DELETE "$DEPLOYMENT_URL/responses/<response_id>" \
> --header "AI-Resource-Group: $AI_RESOURCE_GROUP" \
> --header "Authorization: Bearer $AUTH_TOKEN"
> 
> ```

> ### Output Code:  
> ```
> {
>   "deleted": true,
>   "id": "resp_0f2d32831fb00e2e0069d5f8e804808193b3379a80c7a3b172",
>   "object": "response.deleted"
> }
> ```

