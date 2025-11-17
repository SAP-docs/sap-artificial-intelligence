<!-- loioff33cb8d121f4093901596c55170b815 -->

# Orchestration with Fallbacks

You can define multiple sets of module configurations for completions in your orchestration workflow to incorporate fallbacks in case of processing failure, such as unsupported models in the deployed region. Requests are processed using the configuration with the highest preference. If processing fails, the next preferred configuration is automatically useed for processing. Preference order follows the list sequence: the first item has highest priority, and the last item has lowest priority.

This feature is only available in orchestration V2.



## Criteria for switching to fallback configurations

**For streaming and non-streaming requests:** orchestration switches to fallback configurations when the specified model in the higher-preference instance is not supported in the deployed region.

**For non-streaming requests:** orchestration may also switch to the next fallback if it encounters certain errors during processing. This allows orchestration to leverage fallback configurations and to provide successful responses in case of transient errors, for example, temporary unavailability of a model or service. For streaming requests, switching to a fallback configuration is not straightforward once the stream has started.

Orchestration will only switch to the next defined fallback configuration if it encounters specific errors during processing. For all other errors, orchestration will fail the request and return the corresponding error in the response.

The fallback configuration will be used in the following scenarios::

-   For streaming requests:
    -   If specified model is not supported in the deployed region or environment


-   For non-streaming requests:
    -   If specified model is not supported in the deployed region or environment

    -   If orchestration service encounters any of the following errors during processing:

        -   Client errors: `429 Too Many Requests` and `408 Request Timeout`

        -   All server errors `5xx`






## Example

The following example shows a request with: the specified `modules` list indicating that `gpt-4o` is preferred as the primary model, with `mistralai—mistral-small-instruct` as the fallback option. If `gpt-4o` is unsupported in the deployed region, orchestration automatically switches to the second preference. Module configurations can vary between preferences to suit different use cases. In this case, the fallback configuration omits the filtering module.

> ### Sample Code:  
> ```
> curl --request POST $ORCH_DEPLOYMENT_URL/v2/completion \
> --header 'content-type: application/json' \
> --header "Authorization: Bearer $TOKEN" \
> --header "AI-Resource-Group: $RESOURCE_GROUP" \
> --data-raw '{
>     "config": {
>         "modules": [
>             { //1st prererence
>                "prompt_templating": {
>                     "prompt": {
>                         "template": [
>                             {
>                                 "role": "system",
>                                 "content": "You a language translation model that translates English to German."
>                             },
>                             {
>                                 "role": "user",
>                                 "content": "{{ ?input }}"
>                             }
>                         ]
>                     },
>                     "model": {
>                         "name": "gpt-4o",
>                         "params": {
>                             "max_tokens": 300,
>                             "temperature": 2
>                         }
>                     }
>                 },
>                 "filtering": {
>                     "input": {
>                         "filters": [
>                             {
>                                 "type": "azure_content_safety",
>                                 "config": {
>                                     "prompt_shield": "true"
>                                 }
>                             }
>                         ]
>                     }
>                 }
>             },
>             { //2nd preference
>                 "prompt_templating": {
>                     "prompt": {
>                         "template": [
>                             {
>                                 "role": "system",
>                                 "content": "You a language translation model that translates English to German."
>                             },
>                             {
>                                 "role": "user",
>                                 "content": "{{ ?input }}"
>                             }
>                         ]
>                     },
>                     "model": {
>                         "name": "mistralai--mistral-small-instruct",
>                         "params": {
>                             "max_tokens": 300,
>                             "temperature": 2
>                         }
>                     }
>                 }
>             }
>         ]
>     },
>     "placeholder_values": {
>         "input": "Reply with Orchestration Service is working! in German"
>     }
> }'
> ```

The successful response below was processed using the fallback preference `mistralai—mistral-small-instruct`. The `intermediate_failures` field indicates why the highest preference model was skipped.

> ### Output Code:  
> ```
> {
>     "request_id": "f380e708-cd64-9b87-b36b-03b53a678f59",
>     "intermediate_results": {
>         "templating": [
>             {
>                 "content": "Reply with Orchestration Service is working! in German",
>                 "role": "user"
>             }
>         ],
>         "llm": {
>             "id": "chatcmpl-0d66dbb6-6a3b-9aa5-a2c3-4f4c9e608051",
>             "object": "chat.completion",
>             "created": 1761909762,
>             "model": "mistralai--mistral-small-instruct",
>             "choices": [
>                 {
>                     "index": 0,
>                     "message": {
>                         "role": "assistant",
>                         "content": "Sure! Here is the translation:\n\n\"Orchestration Service läuft!\"\n\nThis means \"Orchestration Service is working!\" in German."
>                     },
>                     "finish_reason": "stop"
>                 }
>             ],
>             "usage": {
>                 "completion_tokens": 30,
>                 "prompt_tokens": 14,
>                 "total_tokens": 44
>             }
>         }
>     },
>     "final_result": {
>         "id": "chatcmpl-0d66dbb6-6a3b-9aa5-a2c3-4f4c9e608051",
>         "object": "chat.completion",
>         "created": 1761909762,
>         "model": "mistralai--mistral-small-instruct",
>         "choices": [
>             {
>                 "index": 0,
>                 "message": {
>                     "role": "assistant",
>                     "content": "Sure! Here is the translation:\n\n\"Orchestration Service läuft!\"\n\nThis means \"Orchestration Service is working!\" in German."
>                 },
>                 "finish_reason": "stop"
>             }
>         ],
>         "usage": {
>             "completion_tokens": 30,
>             "prompt_tokens": 14,
>             "total_tokens": 44
>         }
>     },
>     "intermediate_failures": [
>         {
>             "code": 400,
>             "message": "Model gpt-4o not supported.",
>             "location": "Request Body",
>             "headers": {
>                 "Content-Type": "application/json"
>             }
>         }
>     ]
> }
> ```



## Error Response

If orchestration is unable to process the request using any of the provided fallback module configurations, it responds with a list of errors corresponding to each failed attempt. The overall response code matches the last failed attempt, and the error list follows the defined preference order.

> ### Output Code:  
> ```
> {
>     "error": [// 1st preference        {
>             "request_id": "req-id",
>             "code": 400,
>             "message": "400 - Request Body: Model gpt-4o not supported.",
>             "location": "Request Body",
>             "headers": {
>                 "Content-Type": "application/json"
>             }
>         },
>         {// 2nd preference
>             "request_id": "req-id",
>             "code": 429,
>             "message": "429 - Too many requests.",
>             "location": "LLM",
>             "headers": {
>                 "Content-Type": "application/json",
>                 "x-retry-after": "30"
>             }
>         }
>     ]
> }
> ```

