<!-- loio44463822e86b45a59068dd3acf9aec99 -->

# Input Filtering

The content filtering module is optional and allows you to filter input and output based on content safety criteria. If you don't configure an input filter in the orchestration settings, the input goes to the model configuration without filtering.

The module supports two services:

-   Azure Content Safety
-   Llama Guard 3

The content filtering module allows you to configure multiple distinct filters for a single request. However, each filter type \(such as Azure Content Safety or Llama Guard\) can be configured only once, meaning that you cannot set up two filters of the same type but with different settings. However, different filter types \(such as one Azure and one Llama Guard filter\) can be executed concurrently. The orchestration service will wait for all content filters to complete before returning the results.



<a name="loio44463822e86b45a59068dd3acf9aec99__section_jqr_v5h_tdc"/>

## Azure Content Safety

The Azure Content Safety classification service recognizes four distinct content categories: `Hate`, `Violence`, `Sexual`, and `SelfHarm`. For more information, see [Harm categories in Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/concepts/harm-categories?tabs=warning). Text can have more than one label \(for example, a text sample can be classified as both `Hate` and `Violence`\). The returned content categories include a severity level rating of 0, 2, 4, or 6. The value increases with the severity of the content.

> ### Note:  
> For all Azure OpenAI models, a global content filter is configured on the Azure AI platform. This global filter removes all input and output that is classified as medium \(4\) or high \(6\) in any of the categories.



<a name="loio44463822e86b45a59068dd3acf9aec99__section_fj1_2vh_tdc"/>

## LLama Guard 3

Llama Guard 3 recognizes the following content categories:

-   `violent_crimes`
-   `non_violent_crimes`
-   `sex_crimes`
-   `child_exploitation`
-   `defamation`
-   `specialized_advice`
-   `privacy`
-   `intellectual_property`
-   `indiscriminate_weapons`
-   `hate`
-   `self_harm`
-   `sexual_content`
-   `elections`
-   `code_interpreter_abuse`

For more information, see [Hazard Taxonomy and Policy in Llama Guard 3 8B](https://github.com/meta-llama/PurpleLlama/blob/main/Llama-Guard3/8B/MODEL_CARD.md#hazard-taxonomy-and-policy). Texts can have multiple labels. The returned content categories include a boolean value that shows whether the text contains content triggering the filter for each respective category.

-   **[Enhancing Model Consumption with Input Filtering](enhancing-model-consumption-with-input-filtering-04e7c5a.md "")**  


**Related Information**  


[Enhancing Model Consumption with Input Filtering](enhancing-model-consumption-with-input-filtering-04e7c5a.md "")

