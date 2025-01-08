<!-- loiocdd4847a8ec74b10b980c87843d80027 -->

# Orchestration

Orchestration combines content generation with a set of functions that are often required in business AI scenarios.

Functions include:

-   Templating, which lets you compose a prompt with placeholders that are filled during inference

-   Content filtering, which lets you restrict the type of content that is passed to and received from a generative AI model
-   Data Masking, which lets you mask data via anonymization or pseudonymization before passing it into a genereative AI model. In case of pseudonymization masked data present in the generative AI model response will be unmasked.

-   Grounding, which lets you integrate external, contextually relevant, domain-specific, or real-time data into AI processes. This data supplements the natural language processing capabilities of pre-trained models, which are trained on general material.


-   **[Orchestration Workflow](orchestration-workflow-b233648.md "In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single
		API call. Within the pipeline, the response from one module is used as the input for the next module.")**  
In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.
-   **[Harmonized API](harmonized-api-e99365f.md "The harmonized API lets you use different foundation models without the need to change
		the client code. It does so by taking the OpenAI API as the standard and mapping other model
		APIs to it. This includes standardizing message formats, model parameters, and response
		formats. The harmonized API is integrated into the templating module, the model
		configuration, and the orchestration response.")**  
The harmonized API lets you use different foundation models without the need to change the client code. It does so by taking the OpenAI API as the standard and mapping other model APIs to it. This includes standardizing message formats, model parameters, and response formats. The harmonized API is integrated into the templating module, the model configuration, and the orchestration response.
-   **[Streaming](streaming-3340907.md "")**  

-   **[Model Restriction](model-restriction-4d499ee.md "")**  


