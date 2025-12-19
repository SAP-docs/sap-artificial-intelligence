<!-- loioc45166aed4f74922ac274acaae3e39b3 -->

# Large Language Models

Large Language Models \(LLMs\) are trained on vast amounts of text data to understand and generate human-like language.LLMs are useful for tasks such as text generation, summarization, translation, question answering, and conversational AI.



## SAP AI Core Hosted Models

These are models that are deployed and managed on SAP AI Core infrastructure.

Open Source models are hosted by SAP AI Core and are accessible through an OpenAI-compatible API schema.



## Remote Models

Remote models are hosted on remotely, on external platforms or infrastructures.

Models from Azure OpenAI are accessed through a private instance of the chat-completions API. These access points aren't publicly available and are accessed through SAP AI Core. For more information, see Chat completions in the Microsoft documentation.



## Workflow

You can access LLMs through the `foundation-models` and `orchestration` scenarios.

To use a model through the `foundation-models` scenario, you'll need to know its `executableId`. For more information about available models, region and cost information, and executable IDs, see [Supported Models](supported-models-509e588.md).

Next, create a configuration and deployment using the `foundation-models` and `executableId`. You'll then consume the model through API calls. For more information, see [Create a Deployment](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide-dev/activate-generative-ai-hub-for-sap-ai-core#create-a-deploymentl) and [Consume Models](consume-models-bf0373b.md).

To use a model through the `orchestration` scenario, using the harmonized API, see [Orchestration](orchestration-8d02235.md).

