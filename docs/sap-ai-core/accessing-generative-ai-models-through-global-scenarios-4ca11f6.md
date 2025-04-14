<!-- loio4ca11f687fbd435b813b2726c3ddbaea -->

# Accessing Generative AI Models Through Global Scenarios

Access to generative AI models falls under the global AI scenarios `foundation-models` and `orchestration`. SAP AI Core manages these scenarios. You can access individual models as executables through serving templates. To use a specific model, choose the corresponding template.



<a name="loio4ca11f687fbd435b813b2726c3ddbaea__section_jmy_mng_xdc"/>

## When to Use Orchestration vs. Foundation Models



### Advantages of Using Orchestration

-   Provider Agnostic: The orchestration service offers a unified interface for accessing LLMs from multiple providers, simplifying the process of testing and comparing models. You can switch models via a config parameter without creating new deployments.
-   Simplified Integration: It streamlines the integration of LLMs into applications, ensuring efficient and cost-effective development.
-   Expandability: The service allows you to start with basic features and add modules as needed, offering a smooth learning curve.



### Considerations Before Using Orchestration

-   Function Calling Availability: Function calling, with its structured output aspects, isn't currently available.
-   Open Source Framework Support: While we support LangChain, a popular open-source framework, we can't support every framework available. If a specific open-source framework is required, you might need to extend it for support or consider alternative integration methods.

-   **[Orchestration](orchestration-cdd4847.md "The orchestration service operates under the global AI scenario
			orchestration, which is managed by SAP AI Core. This service
		enables the use of various generative AI models with a unified code, configuration, and
		deployment.")**  
The orchestration service operates under the global AI scenario `orchestration`, which is managed by SAP AI Core. This service enables the use of various generative AI models with a unified code, configuration, and deployment.
-   **[Foundation Models](foundation-models-2d981fb.md "The foundation models service operates under the global AI scenario
			foundation-models, which is managed by SAP AI Core.")**  
The foundation models service operates under the global AI scenario `foundation-models`, which is managed by SAP AI Core.

**Related Information**  


[Orchestration](orchestration-cdd4847.md "The orchestration service operates under the global AI scenario orchestration, which is managed by SAP AI Core. This service enables the use of various generative AI models with a unified code, configuration, and deployment.")

[Foundation Models](foundation-models-2d981fb.md "The foundation models service operates under the global AI scenario foundation-models, which is managed by SAP AI Core.")

