<!-- loiob233648e0696461984410c38448fc81b -->

# Orchestration Workflow

In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.



## Prerequisites

You have created a deployment for orchestration as described at [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loiob233648e0696461984410c38448fc81b__context_a51_5qc_ybc"/>

## Workflow

The order in which the pipeline is executed is defined centrally in orchestration. However, you can configure the details for each module and omit optional modules by passing an orchestration configuration in JSON format with the request body.

**The image below is interactive. Click each part of the workflow for more information.**

![](images/4a_orchstration_workflow_2083f88.png)

-   [Grounding](grounding-454c558.md)
-   [Templating](templating-88c5608.md)
-   [Input Translation](input-translation-c43ad1d.md)
-   [Data Masking](data-masking-8b87002.md)
-   [Input Filtering](input-filtering-4446382.md)
-   [Model Configuration](model-configuration-c1bdb26.md)
-   [Output Filtering](output-filtering-b021a5e.md)
-   [Output Translation](output-translation-8f7fb8e.md)

-   **[Grounding](grounding-454c558.md "Grounding integrates external, contextually relevant, domain-specific, or real-time data
		into AI processes. This data enhances the natural language processing capabilities of
		pretrained models, which are trained on general material.")**  
Grounding integrates external, contextually relevant, domain-specific, or real-time data into AI processes. This data enhances the natural language processing capabilities of pretrained models, which are trained on general material.
-   **[Templating](templating-88c5608.md "")**  

-   **[Input Translation](input-translation-c43ad1d.md "")**  

-   **[Data Masking](data-masking-8b87002.md "The data masking module is optional and serves to anonymize or pseudonymize
		personally identifiable information from the input for selected entities.")**  
The data masking module is optional and serves to anonymize or pseudonymize personally identifiable information from the input for selected entities.
-   **[Input Filtering](input-filtering-4446382.md "")**  

-   **[Model Configuration](model-configuration-c1bdb26.md "")**  

-   **[Output Filtering](output-filtering-b021a5e.md "")**  

-   **[Output Translation](output-translation-8f7fb8e.md "")**  


