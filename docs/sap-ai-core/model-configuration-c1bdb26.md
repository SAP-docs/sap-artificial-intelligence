<!-- loioc1bdb26ca11f4457a183df0940419113 -->

# Model Configuration

The model configuration module is mandatory. It lets you inference the large language module by making a call to the specified LLM and returning its response. You can configure the module by passing the following information:

-   Model Name \(parameter `model_name`\): The model name is required. For information about foundation models and supported models, see [Foundation Models](foundation-models-2d981fb.md) and SAP Note [3437766](https://me.sap.com/notes/3437766).

-   Model Parameters \(parameter `model_params`\): The model parameters are optional. Possible values depend on the chosen model. For more information, see [Harmonized API](harmonized-api-e99365f.md).

    For Anthropic models, however, the parameter `max_tokens` is required. If you don't set a value, the orchestration service sets this parameter to the maximum value allowed by the model. For more information, see the Anthropic documentation at [Models](https://docs.anthropic.com/en/docs/about-claude/models).

-   Model Version \(parameter `model_version`\): The model version is optional and defaults to “latest”.


