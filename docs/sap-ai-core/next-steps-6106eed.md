<!-- loio6106eedb26ad4856a7d60ef9a33222b8 -->

# Next Steps

In the section above, we've outlined the basic steps for model consumption.

If you're interested in exploring advanced use cases for enhancing LLM responses with capabilities like grounding, data masking, and content filtering, see [Orchestration](orchestration-cdd4847.md).

Alternatively, you can deploy and consume models using direct model access. For more information, see [Foundation Models](foundation-models-2d981fb.md).



<a name="loio6106eedb26ad4856a7d60ef9a33222b8__section_jmy_mng_xdc"/>

## When to Use Orchestration vs. Foundation Models



### Advantages of Using Orchestration

-   Provider Agnostic: The orchestration service offers a unified interface for accessing LLMs from multiple providers, simplifying the process of testing and comparing models. You can switch models via a config parameter without creating new deployments.
-   Simplified Integration: It streamlines the integration of LLMs into applications, ensuring efficient and cost-effective development.
-   Expandability: The service allows you to start with basic features and add modules as needed, offering a smooth learning curve.



### Considerations Before Using Orchestration

-   Function Calling Availability: Function calling, with its structured output aspects, isn't currently available.
-   Open Source Framework Support: While we support LangChain, a popular open-source framework, we can't support every framework available. If a specific open-source framework is required, you might need to extend it for support or consider alternative integration methods.

