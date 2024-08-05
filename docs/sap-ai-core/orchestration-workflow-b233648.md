<!-- loiob233648e0696461984410c38448fc81b -->

# Orchestration Workflow

In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.



The order in which the pipeline is executed is defined centrally in orchestration. However, you can configure the details for each module and omit optional modules by passing an orchestration configuration in JSON format with the request body.

![](images/Orchestration_Workflow_f67a8ea.png)



### Templating

The templating module is mandatory. It enables you to compose prompts and define placeholders. It then generates the final query that is sent to the model configuration module. Any placeholders that you define in your prompt can be filled at runtime. For example, the following template places the input text into the `{{ ?input }}` parameter:

```json
"templating_module_config": {
  "template": [
    {
      "role":"user",
      "content":"{{ ?input }}"
    }
  ]
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
}
```



### Input Filtering

The content filtering module is optional. It lets you filter the input and output based on content safety criteria.

The module supports the Azure Content Safety classification service. This service recognizes four distinct content categories: `Hate`, `Violence`, `Sexual`, and `SelfHarm`. For more information, see [Harm categories in Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/concepts/harm-categories?tabs=warning). Text can have more than one label \(for example, a text sample can be classified as both `Hate` and `Violence`\). The returned content categories include a severity level rating of 0, 2, 4, or 6. The value increases with the severity of the content.

> ### Note:  
> For all Azure OpenAI models, a global content filter is configured on the Azure AI platform. This global filter removes all input and output that is classified as medium \(4\) or high \(6\) in any of the categories.

If no content filter is configured in the orchestration configuration, the input is passed to the model configuration without filtering. Similarly, the response is returned without filtering.



### Model Configuration

The model configuration module is mandatory. It lets you inference the large language module by making a call to the specified LLM and returning its response. You can configure the module by passing the following information:

-   Model Name: The name of the model to be used.
-   Model Parameters: The parameters to be applied to the model.
-   Model Version: The version of the model to be used, which can either be latest or a specific version number.



### Output Filtering

The content filtering module is optional. It lets you filter the input and output based on content safety criteria.

The module supports the Azure Content Safety classification service. This service recognizes four distinct content categories: `Hate`, `Violence`, `Sexual`, and `SelfHarm`. For more information, see [Harm categories in Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/concepts/harm-categories?tabs=warning). Text can have more than one label \(for example, a text sample can be classified as both `Hate` and `Violence`\). The returned content categories include a severity level rating of 0, 2, 4, or 6. The value increases with the severity of the content.

> ### Note:  
> For all Azure OpenAI models, a global content filter is configured on the Azure AI platform. This global filter removes all input and output that is classified as medium \(4\) or high \(6\) in any of the categories.

If no content filter is configured in the orchestration configuration, the input is passed to the model configuration without filtering. Similarly, the response is returned without filtering.

