<!-- loiod1972706d69a46acb01873ebe0c54689 -->

# SAP-ABAP-1

`SAP-ABAP-1` is a foundation model built by SAP that helps with coding tasks. It is fine-tuned on a large amount of SAP ABAP code.



## Key Features

Key features include:

-   **Pretrained Model:** The model is fine-tuned on the SAP S/4HANA ABAP and CDS code base. There's no need to collect, prepare, or manage training data. You also don't need to manage costly compute infrastructure for training.

-   **Code Explanation:** The model helps you to understand code by turning code to text. For more information, see [Using SAP-ABAP-1 to Explain Code](sap-abap-1-d197270.md#loiod1972706d69a46acb01873ebe0c54689__ABAP_text_to_code).

-   **Integration:** You can integrate the model into development tools, IDEs, or agentic frameworks.

-   **Access to SAP Internal Models:** You gain direct access to the model used internally for the SAP Joule for developers feature in ADT. The same model is also used for SAP Joule for Consultants and the Custom Code Migration scenario, which explains old code to users during the migration from SAP ERP to SAP S/4HANA.




<a name="loiod1972706d69a46acb01873ebe0c54689__section_access_sap_abap_1"/>

## Accessing SAP-ABAP-1

`SAP-ABAP-1` can only be accessed via the Orchestration service of the generative AI hub. Make sure you have met the following prerequisites before you start:

-   You are onboarded to SAP AI Core and have an SAP AI Core service instance and service key. For more information, see [Initial Setup](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/38c4599432d74c1d94e70f7c955a717d.html "Get started with SAP AI Core using the standard procedures for the SAP BTP, Cloud Foundry environment or Kyma environment.") :arrow_upper_right:.

-   You are using the extended service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right: and [Update a Service Plan](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/924f892e67b7443fbb4476b3e81959b2.html "Update your SAP AI Core service instance from the free plan to a standard or extended plan while keeping your data and models.") :arrow_upper_right:.

-   You have completed the client authorization for your preferred user interface. For more information, see [Use a Service Key](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/3a97465bf6164400a4b5c1641007e3d6.html "After you have created your service key, it can be used by local clients, apps in other spaces, or entities outside your deployment to access SAP AI Core through one of the available interfaces.") :arrow_upper_right:.

-   You have obtained your Orchestration service deployment URL. For more information, see [Get An Orchestration Deployment URL](get-an-orchestration-deployment-url-ec7c703.md).


You can submit a test call to `SAP-ABAP-1` using the Orchestration service. To do so, use `sap-abap-1` as the `model_name` in the request payload.



<a name="loiod1972706d69a46acb01873ebe0c54689__ABAP_text_to_code"/>

## Using SAP-ABAP-1 to Explain Code

After you have met the prerequisites, you can make inference calls. `SAP-ABAP-1` supports the code-to-text scenario. The input is an ABAP class or a code snippet from your ABAP code repository. The output is an explanation in English of this class or code snippet.

For more information about how to make inference calls, see [Example Payloads for Inferencing: SAP-ABAP-1](example-payloads-for-inferencing-sap-abap-1-9ea7333.md).



### Context Length

The maximum context length is 128,000 tokens. Considering the need to reserve some context length for prompt instructions and output, the maximum input code size is approximately 120,000 tokens. This corresponds to roughly 250,000 input code characters.



### Input/Output Filtering

Input and output filtering is configured for the model to prevent malicious or harmful content being included in the input or output.



## FAQ

1.  **What is the relationship between `SAP-ABAP-1` and the SAP Joule for developers feature in the ABAP Development Tools for Eclipse?**

    `SAP-ABAP-1` is used internally for the SAP Joule for developers feature in the ABAP Development Tools for Eclipse.

2.  **Can `SAP-ABAP-1` also be used to generate code?**

    The current version of `SAP-ABAP-1` is optimized for explaining ABAP code. It can also generate code, but this capability is experimental and not recommended for productive use. You're welcome to explore code generation, but please note that it's not the primary focus of the model.

3.  **Can the model be integrated into the ABAP Development Tools for Eclipse, VS Code, or other IDEs?**

    The model is natively integrated into the ABAP Development Tools for Eclipse \(ADT\) as part of SAP Joule for developers. Currently, there isn't an out-of-the-box integration for VS Code. However, it's technically possible to integrate with any IDE that has extension interfaces.

4.  **Is it possible to access the model weights for further fine-tuning?**

    No, currently `SAP-ABAP-1` is only accessible through the Orchestration service of the generative AI hub.

5.  **Can I test `SAP-ABAP-1` for free?**

    Yes, you can test the model for 30 days free of charge by using the “Try now” feature. For more information, see [Generative AI Hub](https://www.sap.com/germany/products/artificial-intelligence/generative-ai-hub.html).


-   **[Example Payloads for Inferencing: SAP-ABAP-1](example-payloads-for-inferencing-sap-abap-1-9ea7333.md "")**  

-   **[Prompting Templates](prompting-templates-214c3c3.md "")**  


**Parent topic:**[Models](models-6440777.md "")

**Related Information**  


[Large Language Models](large-language-models-c45166a.md "Large Language Models (LLMs) are trained on vast amounts of text data to understand and generate human-like language.LLMs are useful for tasks such as text generation, summarization, translation, question answering, and conversational AI.")

[SAP-RPT-1](sap-rpt-1-f128f5e.md "SAP-RPT-1 is a relational pretrained transformer for use on relational and structured data. It's developed and maintained by SAP.")

[Supported Models](supported-models-509e588.md "")

[Example Payloads for Inferencing: SAP-ABAP-1](example-payloads-for-inferencing-sap-abap-1-9ea7333.md "")

