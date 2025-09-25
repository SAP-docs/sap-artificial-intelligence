<!-- loio29b17dffb5524eeb85935c3546a80168 -->

# Translation

Thetranslation module is optional. It allows you to translate LLM text prompts into a chosen target language.

The input translation module helps improve answer quality when the configured model performs better with input in a specific language, for example English.

The output translation module is optional. It allows you to translate LLM output into a chosen target language.

To use translation, configure it as part of your orchestration workflow.

The module supports SAP's Document Translation service \(part of the SAP Translation Hub\).

> ### Caution:  
> Input translation is performed **before** any configured input masking. Any content added to the prompt as part of prompt templating is sent to the translation service unmodified. Output translation is performed **after** any configured output unmasking. Unmasked output is sent to the translation service.

-   **[Enhance Model Consumption with Input Translation](enhance-model-consumption-with-input-translation-152a5f4.md "")**  

-   **[Enhance Model Consumption with Output Translation](enhance-model-consumption-with-output-translation-48be058.md "")**  


**Related Information**  


[Enhance Model Consumption with Input Translation](enhance-model-consumption-with-input-translation-152a5f4.md "")

[Enhance Model Consumption with Output Translation](enhance-model-consumption-with-output-translation-48be058.md "")

