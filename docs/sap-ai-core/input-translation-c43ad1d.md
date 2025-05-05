<!-- loioc43ad1d2dfed4a7e87e3dfd3c68b111f -->

# Input Translation

The input translation module is optional. It allows you to translate LLM text prompts into a chosen target language.

The input translation module helps improve answer quality when the configured model performs better when input is provided in a specific language, for example English.

To use input translation, configure it as part of your orchestration workflow.

The module supports SAP's Document Translation service \(part of the SAP Translation Hub\).

> ### Caution:  
> Input translation is performed **before** any configured input masking. Any content added to the prompt as part of prompt templating is sent to the translation service unmodified.

-   **[Enhance Model Consumption with Input Translation](enhance-model-consumption-with-input-translation-0291151.md "")**  


