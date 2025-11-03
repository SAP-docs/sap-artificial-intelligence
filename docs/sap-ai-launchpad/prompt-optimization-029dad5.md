<!-- loio029dad5ebaea4b9595d32b3437cd3fea -->

# Prompt Optimization

Prompt Optimization utilizes an input prompt template from the prompt registry and a JSON dataset in the object store containing desirable responses. It optimizes the input prompt to maximize a specified metric, with metrics tracked in the ML Tracking Service. The resulting optimized prompt is saved back to the prompt registry, and additional result information is stored in the object store. This optimization process is model-specific to accommodate different model behaviors and is executed as a distinct run.

> ### Note:  
> Prompt optimization executions can take from minutes to multiple hours to run, and will submit a large number of prompt requests to the target models.

> ### Restriction:  
> Mistral and DeepSeek models are not supported for prompt optimization.

![](images/prompt_optimization_b6e6b8f.png)

-   **[Create a Prompt Optimization](create-a-prompt-optimization-0b920f6.md "
		
	")**  

-   **[View Prompt Optimizations](view-prompt-optimizations-3a8374a.md "")**  

-   **[View Prompt Optimization Run Details](view-prompt-optimization-run-details-acfce87.md "")**  


