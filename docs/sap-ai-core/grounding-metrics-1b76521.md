<!-- loio1b76521a8c2943938130b2a66acb601f -->

# Grounding Metrics

To use grounding related metrics, at least one of your runs provided should have `grounding_module_config` field present in your run configuration file. For more information, see [Grounding](grounding-035c455.md).

Grounding integrates external, contextually relevant, domain-specific, or real-time data into AI processes. User provided context documents enhance the natural language processing capabilities of pretrained models, which are trained on general material.

This process involves an information retrieval component, where contextually relevant information is identified and retrieved and a generative component, where contextually relevant information is rewritten in line with the user query.

Evaluating a grounding system involves assessing both the retrieval and generation components to ensure they work together effectively.

You can evaluate your grounding pipelines using the metrics in this section.

-   **[Metric Validation](metric-validation-30c8ff8.md "")**  

-   **[Computed Metrics vs LLM-as-a-Judge Metrics](computed-metrics-vs-llm-as-a-judge-metrics-c148a1e.md "")**  


