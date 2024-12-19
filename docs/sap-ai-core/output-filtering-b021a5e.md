<!-- loiob021a5e4e3ae433e9f5250cec058efd9 -->

# Output Filtering

The content filtering module is optional. It lets you filter the input and output based on content safety criteria.

The module supports the Azure Content Safety classification service. This service recognizes four distinct content categories: `Hate`, `Violence`, `Sexual`, and `SelfHarm`. For more information, see [Harm categories in Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/concepts/harm-categories?tabs=warning). Text can have more than one label \(for example, a text sample can be classified as both `Hate` and `Violence`\). The returned content categories include a severity level rating of 0, 2, 4, or 6. The value increases with the severity of the content.

> ### Note:  
> For all Azure OpenAI models, a global content filter is configured on the Azure AI platform. This global filter removes all input and output that is classified as medium \(4\) or high \(6\) in any of the categories.

If no content filter is configured in the orchestration configuration, the input is passed to the model configuration without filtering. Similarly, the response is returned without filtering.If no severity levels are set in the configuration \(i.e. the `config` key is not given\), the default level of 2 \(low\) is used for all categories.

