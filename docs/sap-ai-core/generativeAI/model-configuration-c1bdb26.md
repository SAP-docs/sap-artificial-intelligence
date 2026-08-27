<!-- loioc1bdb26ca11f4457a183df0940419113 -->

# Model Configuration

The model configuration module is mandatory. It lets you inference the large language module by making a call to the specified LLM and returning its response. You can configure the module by passing the following information:

-   Model Name \(parameter `model_name`\): The model name is required. For information about foundation models and supported models, see [Foundation Models](foundation-models-2d981fb.md) and SAP Note [3437766](https://me.sap.com/notes/3437766).

-   Model Parameters \(parameter `model_params`\): The model parameters are optional. Possible values depend on the chosen model. For more information, see [Harmonized API](harmonized-api-e99365f.md).

    For Anthropic models, however, the parameter `max_tokens` is required. If you don't set a value, the orchestration service sets this parameter to the maximum value allowed by the model. For more information, see the Anthropic documentation at [Models](https://docs.anthropic.com/en/docs/about-claude/models).

-   Model Version \(parameter `model_version`\): The model version is optional and defaults to “latest”.

-   Timeout \(parameter `timeout`\): is optional and is specified in seconds. Min: 1, max 600, default: 600.

    You can use timeout to configure a timeout limit for LLM calls. 

    Orchestration will either retry or fail the request with a read timeout error \(408\) if the timeout elapses.

    For streaming requests, the timeout represents the entire duration of the streaming response, from connection establishment until the stream is either completely consumed or closed.

    This parameter is ignored by Vertex AI models.

-   Max retries \(parameter `max_retries`\): is optional and is specified in number of retries. Min: 0, max 5, default: 2.

    You can use max\_retries to configure a number of retries for LLM calls. Retries are attempted in case of errors related to connection, network and read timeouts, for example.

    For streaming requests, retries are only attempted when establishing the initial connection. Retries are not attempted after streaming responses have started.

    This parameter is ignored by Vertex AI models.




<a name="loioc1bdb26ca11f4457a183df0940419113__section_sxp_1ph_lgc"/>

## Example

```
"llm_module_config": {
    "model_name": "gpt-4o",
    "model_version": "latest",
    "model_params": {...},
    "timeout": 10
    "max_retries": 3
}
```

