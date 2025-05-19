<!-- loio88c5608ca13f4ae18d466947907b46e0 -->

# Templating

The templating module is mandatory. It enables you to compose prompts and define placeholders. It then generates the final query that is sent to the model configuration module. Any placeholders that you define in your prompt can be filled at runtime. For example, the following template places the input text into the `{{ ?input }}` placeholder:

```json
"templating_module_config": {
  "template": [
    {
      "role": "user",
      "content": "{{ ?input }}"
    }
  ]
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
"templating_module_config": {
  "template": [
    {
      "role": "user",
      "content": "Create {{ ?number }} paraphrases of {{ ?phrase }}"
    }
  ],
  "defaults": {
    "number": 5
  }
},
//... other configuration
"input_params": {
  "number": "3",
  "phrase": "Please respond as soon as possible, thanks."
}
```

Templates can also be retrieved from the prompt registry. For more information, see [Prompt Registry](prompt-registry-5392e7d.md).

Templates can be retrieved by ID \(immutable\) or the combination of scenario, name, and version \(mutable\). For examples:

> ### Sample Code:  
> ```
> "templating_module_config":{
>   "template_ref":{
>     "id": "d22342e7-1f91-4c52-a794-04833bc2574a"
>     }
> },
> 
> ```
> 
> or
> 
> ```
> 
> "templating_module_config":{
>   "template_ref":{
>     "scenario": "<scenario>",
>     "name": "<name>",
>     "version": "semver version e.g. 0.0.1 or `latest`"
>   }
> },
> ```



<a name="loio88c5608ca13f4ae18d466947907b46e0__section_bm3_5jp_4dc"/>

## Input Image Support

Images can be provided as additional input where supported.

For example:

> ### Sample Code:  
> ```
>  "template": [
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

The URL for the image supports Base64 or a web-based URL of the image. Check with the model provider that your preferred upload method is supported.

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

-   **[Few-Shot Learning](few-shot-learning-4fe47b1.md "")**  

-   **[Chat](chat-39321a9.md "Orchestration can also be used in chat scenarios. The following example shows how to configure the templating module to use a chat
		prompt.")**  
Orchestration can also be used in chat scenarios. The following example shows how to configure the templating module to use a chat prompt.
-   **[Minimal Call](minimal-call-949e773.md "")**  

-   **[Tool Calling](tool-calling-f959929.md "")**  


