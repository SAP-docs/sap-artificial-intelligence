<!-- loio3e2ea66d870043c6b0046ce41850c87e -->

# Templating

The templating module is mandatory. It enables you to:

-   Compose prompts
-   Define placeholders
-   Confgure your chosen LLM

Your template generates the final query and inferences your specified LLM.

You can configure the module by passing the following information:

-   Model Name \(parameter `name`\): The model name is required. For information about foundation models and supported models, see [Foundation Models](foundation-models-2d981fb.md) and SAP Note [3437766](https://me.sap.com/notes/3437766).

-   Model Parameters \(parameter `params`\): The model parameters are optional. Possible values depend on the chosen model. For more information, see [Harmonized API](harmonized-api-e99365f.md).

    For Anthropic models, however, the parameter `max_tokens` is required. If you don't set a value, the orchestration service sets this parameter to the maximum value allowed by the model. For more information, see the Anthropic documentation at [Models](https://docs.anthropic.com/en/docs/about-claude/models).

-   Model Version \(parameter `version`\): The model version is optional and defaults to “latest”.

-   Timeout \(parameter `timeout`\): is optional and is specified in seconds. Min: 1, max 600, default: 600.

    You can use timeout to configure a timeout limit for LLM calls. 

    Orchestration will either retry or fail the request with a read timeout error \(408\) if the timeout elapses.

    For streaming requests, the timeout represents the entire duration of the streaming response, from connection establishment until the stream is either completely consumed or closed.

    This parameter is ignored by Vertex AI models.

-   Max retries \(parameter `max_retries`\): is optional and is specified in number of retries. Min: 0, max 5, default: 2.

    You can use max\_retries to configure a number of retries for LLM calls. Retries are attempted in case of errors related to connection, network and read timeouts, for example.

    For streaming requests, retries are only attempted when establishing the initial connection. Retries are not attempted after streaming responses have started.

    This parameter is ignored by Vertex AI models.


Any placeholders that you define in your prompt can be filled at runtime. For example, the following template places the input text into the `{{ ?input }}` placeholder:

```json
 "prompt_templating": {
          "prompt": {
            "template": [
            {
              "role": "user",
              "content": "{{?input}}"
            }
          ]
          },
          "model": {
            "name": "gpt-4o",
            "params": {
              "max_tokens": 300,
              "temperature": 2
            }
            "timeout": 10     // in seconds
            "max_retries": 3
         }
        }
```

The `{{ ?input }}` placeholder is filled using the contents of the `input_params.input` parameter:

```
"input_params": {
  "input": "A sample prompt to be sent to the model"
}
```

You can also set default values for the placeholders. For example, to request either 5 paraphrases or a user-specific number of paraphrases for a given phrase, you can use the following configuration:

```json
{
  "prompt_templating": {
    "prompt": {
      "template": [
        {
          "role": "user",
          "content": "Create {{ ?number }} paraphrases of {{ ?phrase }}"
        }
      ],
      "defaults": {
        "number": 5
      }
    }
  },
  //... other configuration

    "placeholder_values": {
      "number": "3",
      "phrase": "Hello."
    }

}
```

Templates can also be retrieved from the prompt registry. For more information, see [Prompt Registry](prompt-registry-5392e7d.md).

Templates can be retrieved by ID \(immutable\) or the combination of scenario, name, and version \(mutable\). For examples:

> ### Sample Code:  
> ```
> "prompt_templating": {
>           "prompt": {
>               "template_ref": {
>                   "id": "d22342e7-1f91-4c52-a794-04833bc2574a"
>          }
>     }
> },
> 
> ```
> 
> or
> 
> ```
> 
> "prompt_templating": {
>           "prompt": {
>               "template_ref": {
>                   "scenario": "test-scenario",
>                   "name": "test-template",
>                   "version": "0.0.1"
>               }
>           }
>  },
> ```



<a name="loio3e2ea66d870043c6b0046ce41850c87e__section_bm3_5jp_4dc"/>

## Input Image Support

Images can be provided as additional input where supported.

For example:

> ### Sample Code:  
> ```
>  "messages_history": [
>     {"role": "system", "content": "You are a helpful assistant."},
>     {
>         "role": "user",
>         "content": [
>             {"type": "text", "text": "what is in this image?"},
>             {"type": "image_url", "image_url": {"url": "..."}},
>             ],
>         },
>       
> ],
> ```

The URL for `image_url` supports Base64 or a web-based URL of the PDF. Check with the model provider that your preferred upload method is supported.

```
"image_url": {
    "url":  f"data:image/jpeg;base64,{base64_image}"
}
```

or

```
 "image_url": {
    "url": "https://some.jpg"
}
```



## Input PDF Support

PDFs can be provided as additional input for Gemini models only.

```
{
  "config": {
    "modules": {
      "prompt_templating": {
        "model": {
          "name": "gemini-2.5-flash",
          "params": {
            "temperature": 0.1
          }
        },
        "prompt": {
          "template": [
            {
              "role": "user",
              "content": [
                {
                  "type": "image_url",
                  "image_url": {
                    "url": "data:application/pdf;base64,{{?base64_pdf}}"
                  }
                },
                {
                  "type": "text",
                  "text": "what does the document say?"
                }
              ]
            }
          ]
        }
      }
    },
    "stream": {
      "enabled": false
    }
  },
  "placeholder_values": {
    "base64_pdf": "JVBERi0xLjQKMSAwIG9iago8PC9UeXBlIC9DYXRhbG9nCi9QYWdlcyAyIDAgUgo+PgplbmRvYmoKMiAwIG9iago8PC9UeXBlIC9QYWdlcwovS2lkcyBbMyAwIFJdCi9Db3VudCAxCj4+CmVuZG9iagozIDAgb2JqCjw8L1R5cGUgL1BhZ2UKL1BhcmVudCAyIDAgUgovTWVkaWFCb3ggWzAgMCA1OTUgODQyXQovQ29udGVudHMgNSAwIFIKL1Jlc291cmNlcyA8PC9Qcm9jU2V0IFsvUERGIC9UZXh0XQovRm9udCA8PC9GMSA0IDAgUj4+Cj4+Cj4+CmVuZG9iago0IDAgb2JqCjw8L1R5cGUgL0ZvbnQKL1N1YnR5cGUgL1R5cGUxCi9OYW1lIC9GMQovQmFzZUZvbnQgL0hlbHZldGljYQovRW5jb2RpbmcgL01hY1JvbWFuRW5jb2RpbmcKPj4KZW5kb2JqCjUgMCBvYmoKPDwvTGVuZ3RoIDUzCj4+CnN0cmVhbQpCVAovRjEgMjAgVGYKMjIwIDQwMCBUZAooRHVtbXkgUERGKSBUagpFVAplbmRzdHJlYW0KZW5kb2JqCnhyZWYKMCA2CjAwMDAwMDAwMDAgNjU1MzUgZgowMDAwMDAwMDA5IDAwMDAwIG4KMDAwMDAwMDA2MyAwMDAwMCBuCjAwMDAwMDAxMjQgMDAwMDAgbgowMDAwMDAwMjc3IDAwMDAwIG4KMDAwMDAwMDM5MiAwMDAwMCBuCnRyYWlsZXIKPDwvU2l6ZSA2Ci9Sb290IDEgMCBSCj4+CnN0YXJ0eHJlZgo0OTUKJSVFT0YK"
  }
}
```

The URL for `image_url` also a web-based URL of the PDF.

```
 "image_url": {
    "url": "https://assets.anthropic.com/m/1cd9d098ac3e6467/original/Claude-3-Model-Card-October-Addendum.pdf"
}
```

-   **[Few-Shot Learning](few-shot-learning-7ffdf9a.md "")**  

-   **[Chat](chat-cd16d73.md "Orchestration can also be used in chat scenarios. The following example shows how to configure the templating module to use a chat
		prompt.")**  
Orchestration can also be used in chat scenarios. The following example shows how to configure the templating module to use a chat prompt.
-   **[Minimal Call](minimal-call-663f1b7.md "")**  

-   **[Tool Calling](tool-calling-2e47871.md "")**  


