<!-- loio33409072eac14f0d96b23e21a0d85bff -->

# Streaming

Streaming is optional. Where models support streaming, output is generated in chunks, and passed through the modules in the orchestration workflow. This is useful for applications such as chatbots, where interactions with the model happen in real time.

> ### Caution:  
> Streaming can increase the number of calls, increasing consumption and associated costs. For example, if a text of 500 characters generates 5 chunks of 100 characters each, the content filtering module receives 5 calls instead of one.
> 
> Streaming can decrease the accuracy of filtering and unmasking, because smaller chunks contain less context. Benchmarking and testing with actual use case data is recommended to ensure output quality in relation to chunk size.
> 
> For more information, see [Metering and Pricing for Generative AI](metering-and-pricing-for-generative-ai-41e8d85.md) and [SAP Note 3505347](https://me.sap.com/notes/3505347).



<a name="loio33409072eac14f0d96b23e21a0d85bff__section_pzr_3pn_xcc"/>

## Activate Streaming

Streaming is set to `false` by default, and is part of the `orchestration_config`. To activate streaming, set `stream` to `true`. For example:

> ### Sample Code:  
> ```
> {
>   "orchestration_config": {
> 	"stream": true,
> 	"module_configurations": {
>         ...
>      },
>      "input_params": {
>         ...
>      }
>   }
> }
> ```

You can configure streaming behavior in the following ways:

-   Chunk Size
-   Delimiters



### Configure Streaming Using Chunk Size

The `chunk_size` parameter defines the maximum number of characters contained in a single chunk, and takes an integer value.

This means that if a model produces chunks that are larger than the configured `chunk_size`, the Orchestration Service will emit these chunks as is, instead of splitting them into multiple chunks.

This minimizes latency and maximizes the context provided to subsequent tasks like content filtering.

The default value for `chunk_size` is 100.

You can configure the `chunk_size` using the `stream_options` parameter in the `orchestration_config`:

The following example shows a streaming configuration with chunk size of 200 characters.

> ### Sample Code:  
> ```
> {
>    "orchestration_config": {
>       "stream": true,
>       "stream_options": {
>          "chunk_size": 200
>       },
>       "module_configurations": {
>          ...
>          "filtering_module_config": {
>             "output": {
>                "filters": [
>                   ...
>                ],
>                "stream_options": {
>                   "overlap": 10
>                }
>             }
>          }
>          ...
>      },
>      "input_params": {
>         ...
>      }
>   }
> }
> ```



### Configure Streaming Using Delimiters

Delimiters can be specified alternatively to, or in addition to chunk size. Streaming configured with the `delimiters` parameter respects the `chunk_size` parameter, but determines the end of a chunk based on the next delimiter in the list, instead of chunk size alone. This means that chunks can be determined in a more meaningful way, for example, to include whole sentences, which may improve output translation, filtering and unmasking results.

You can configure the delimiters using the`stream_options` parameter in the`orchestration_config`:

The following example shows a streaming configuration with delimiters set to common English language sentence endings.

> ### Sample Code:  
> ```
> {
>   "orchestration_config": {
>     "stream": true,
>     "stream_options": {
>       "delimiters": [".", "!", "?"]
>     },
>     "module_configurations": {
>       ...
>     },
>     "input_params": {
>       ...
>   }
> }
> ```



<a name="loio33409072eac14f0d96b23e21a0d85bff__section_azg_fkf_xcc"/>

## Module Specific Streaming Behavior

The following orchestration modules use content passed from streaming:

-   Data Masking \(unmasking pseudonymization only\)

-   Output filtering




### Data Masking

For the data masking module, the full `MASKED_ENTITY_DIGIT` tag is needed for unmasking. When a tag is split by chunking, the entire tag is moved to the following chunk, changing the chunk size.

For example, two chunks containing:

> ### Sample Code:  
> ```
> Yesterday, I spent time with MASKED_PER
> SON_1 discussing the changes
> ```

Would become:

> ### Sample Code:  
> ```
> Yesterday, I spent time with 
> MASKED_PERSON_1 discussing the changes
> ```

This may affect behavior of future modules that are executed after unmasking.



### Output filtering

The `overlap` parameter defines the number of characters at the end of a chunk, that are repeated at the beginning of the next chunk. It takes an integer value. The default value is 0.

Increasing the context window improves output filtering results, but increasing chunk size can affect streaming experience negatively. Overlap repeats a specified amount of text across two adjacent chunks, creating a larger context window, without increasing chunk size.

For example:

> ### Sample Code:  
> ```
> "This is the text from the 1st chunk."
> "This is the text from the 2nd chunk"
> ```

Would become:

> ### Sample Code:  
> ```
> "This is the text from the 1st chunk."
> "the 1st chunk. This is the text from the 2nd chunk"
> ```

You can configure the `overlap` parameter using the `output` \> `stream_options` \> `overlap parameter` in the`filtering_module_config`.

The following example shows a streaming configuration with an overlap of 10 characters.

> ### Sample Code:  
> ```
> {
>    "orchestration_config": {
>       "stream": true,
>       "stream_options": {
>          "chunk_size": 200
>       },
>       "module_configurations": {
>          ...
>          "filtering_module_config": {
>             "output": {
>                "filters": [
>                   ...
>                ],
>                "stream_options": {
>                   "overlap": 10
>                }
>             }
>          }
>          ...
>      },
>      "input_params": {
>         ...
>      }
>   }
> }
> ```



<a name="loio33409072eac14f0d96b23e21a0d85bff__section_e5n_skf_xcc"/>

## Streaming Response Format

Streaming responses follow the conventions used by OpenAI models and are sent as Server-Sent Events \(SSEs\).

The first chunk always contains the module results of all modules executed before calling the LLM.

The LLM's output starts from the second chunk, and each chunk produced by orchestration sends a data event followed by a newline.

Successful responses are terminated with `[DONE]`. If an error occurs, orchestration sends a data event containing an error object as payload, and doesn't terminate with `[DONE]`.



### Example for a Successful Response

The first data event contains the module result of modules that are run before the LLM access. This example shows the templating module result, and an empty orchestration result:

> ### Output Code:  
> ```
> data: {
>   "request_id": "...", 
>        "module_results": {
>          "templating": [
>            {
>              "role": "user", 
>              "content": "Create 3 paraphrases of I love you."}
>          ]
>        }, 
>        "orchestration_result": {
>          "id": "", 
>          "object": "", 
>          "created": 0, 
>          "model": "", 
>          "system_fingerprint": "", 
>          "choices": [
>            {
>              "index": 0, 
>              "delta": {
>                "role": "", 
>                "content": ""
>              }, 
>              "finish_reason": ""
>            }
>          ]
>        }
>       }
> ```

The second and following data events contain module results from the LLM and following modules. This example shows results for LLM access and orchestration. The orchestration result is given in two chunks.

First chunk:

> ### Output Code:  
> ```
> data: {
>   "request_id": "...", 
>   "module_results": {
>     "llm": 
>     {
>       ...
>     }
>   }, 
>   "orchestration_result": {
>     "id": "...", 
>     "object": "chat.completion.chunk", 
>     "created": 1728043660, 
>     "model": "<ModelName>", 
>     "choices": [
>       {
>         "index": 0, 
>         "delta": {
>           "role": "assistant", 
>           "content": "1. My affection for you knows no bounds.\n2. You hold a special place in my heart.\n3. You mean the wo"
>         }, 
>         "finish_reason": ""
>       }
>     ]
>   }
> }
> ```

Second chunk:

> ### Output Code:  
> ```
> data: {
>   "request_id": "163ea321-8f4f-4d00-9b34-7603f1499c24", 
>   "module_results": {
>     "llm": {
>       ...
>     }
>   }, 
>   "orchestration_result": {
>     "id": "...", 
>     "object": "chat.completion.chunk", 
>     "created": 1728043660, 
>     "model": "<ModelName>", 
>     "choices": [
>       {
>         "index": 0, 
>         "delta": {
>           "role": "assistant", 
>           "content": "rld to me."
>         }, "finish_reason": "stop"
>       }
>     ]
>   }
> }
> ```

The final data-event contains `[DONE]`:

> ### Output Code:  
> ```
> 
> data: [DONE]
> ```



### Example for an Error Response

> ### Sample Code:  
> ```
> data: {"json": "payload"}
> 
> data: {"code": 500, "message": "message"}
> ```

