<!-- loiof80417519ea04adb86f7169ae871f884 -->

# Content Filtering

The content filtering module is optional and allows you to filter input and output based on content safety criteria. If you don't configure an input filter in the orchestration settings, the input goes to the model configuration without filtering. If you don't configure an output filter in the orchestration settings, the response returns without any filtering.

The module supports two services:

-   Azure Content Safety
-   Llama Guard 3

The content filtering module allows you to configure multiple distinct filters for a single request. However, each filter type \(such as Azure Content Safety or Llama Guard\) can be configured only once, meaning that you cannot set up two filters of the same type but with different settings. However, different filter types \(such as one Azure and one Llama Guard filter\) can be executed concurrently. The orchestration service will wait for all content filters to complete before returning the results.



<a name="loiof80417519ea04adb86f7169ae871f884__section_jqr_v5h_tdc"/>

## Azure Content Safety



### Harm Categories

The Azure Content Safety classification service recognizes the following distinct content categories: `Hate`, `Violence`, `Sexual`, and `SelfHarm`. For more information, see [Harm categories in Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/concepts/harm-categories?tabs=warning). Text can have more than one label \(for example, a text sample can be classified as both `Hate` and `Violence`\). The returned content categories include a severity level rating of 0, 2, 4, or 6. The value increases with the severity of the content.

> ### Note:  
> For all Azure OpenAI models, a global content filter is configured on the Azure AI platform. This global filter removes all input and output that is classified as medium \(4\) or high \(6\) in any of the categories.



### Prompt Attack Detection

The Azure Content Safety service also supports prompt attack detection for input text via `PromptShield` configuration. For more information see [Prompt Shields in Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/concepts/jailbreak-detection).

A prompt attack is a malicious input that is designed to bypass a model's safety mechanisms or override previous instructions. Prompt attacks can lead to the generation of harmful content or the execution of malicious actions. The Azure Content Safety service detects prompt attacks and returns a Boolean value.

If both prompt attack detection and harm classification are configured, the orchestration service performs the prompt attack detection call first, and then performs the harm classification call. If a prompt attack is detected, the orchestration service does not make the harm classification request and returns the prompt attack detection result only.



### Protected Material Detection for Code

The Azure Content Safety service includes an output content filter that identifies code matching existing GitHub repository code.

The filter scans publicly available code, and has a knowledge cutoff date. Only code matching publicly available code added to GitHub after the knowledge cutoff date can be detected.

For more information see [Protected Material Detection for Code in Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/quickstart-protected-material-code?pivots=programming-language-rest).

> ### Remember:  
> When multiple content filtering types are configured together, each type is processed as a separate request. Costs will be incurred for each filtering type applied.



<a name="loiof80417519ea04adb86f7169ae871f884__section_fj1_2vh_tdc"/>

## Llama Guard 3

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

> ### Note:  
> Llama Guard 3 8B can report violations for categories that have not been requested by the user
> 
> The orchestration service doesn't take these violations into account when processing Llama Guard responses, and only filters violations in categories that have been requested by the user.

-   **[Enhancing Model Consumption with Input Filtering](enhancing-model-consumption-with-input-filtering-75c6d42.md "")**  

-   **[Enhancing Model Consumption with Output Filtering](enhancing-model-consumption-with-output-filtering-0675b9c.md "")**  


**Related Information**  


[Enhancing Model Consumption with Input Filtering](enhancing-model-consumption-with-input-filtering-04e7c5a.md "")

[Enhancing Model Consumption with Output Filtering](enhancing-model-consumption-with-output-filtering-0675b9c.md "")

