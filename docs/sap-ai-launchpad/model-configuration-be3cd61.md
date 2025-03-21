<!-- loiobe3cd61a58514a958de988f0dd8bea57 -->

# Model Configuration

In this section, you select the model that you want to use in your workflow. If you don't select a model, the default model will be used. You can also include further parameters in JSON format. For information about the supported parameters, see the documentation of the model provider.

You can see which models are available within an orchestration deployment by selecting the deployment ID.

![](images/configure_chat_4732b30.png)

When you run the workflow, you will receive one response from the model. If you want to receive multiple responses, you can set a value for the `n` parameter in the model configuration.

> ### Example:  
> If you enter `"n":3` in the model configuration, the model will generate three different responses based on your prompt template.

![](images/modelconfig9b_6c20e83.png)

> ### Note:  
> For models from Anthropic, the `max_tokens` parameter is mandatory and is added to *additional parameters* automatically. Users can update the parameter value, but the parameter should not be removed.

