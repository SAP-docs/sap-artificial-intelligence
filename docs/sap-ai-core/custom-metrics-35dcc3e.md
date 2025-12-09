<!-- loio35dcc3e40136478e8add299389334e25 -->

# Custom Metrics

In addition to system-defined evaluation metrics, you can define custom metrics to evaluate a specific use-case.

LLM-as-a-judge-type metrics are supported. A custom LLM-as-a-judge metric uses a judge LLM along with a rubric to compute a metric rating. The output can be in numeric or text format.

You can define custom LLM-as-a-judge metrics using either structured prompts or free form prompts.



<a name="loio35dcc3e40136478e8add299389334e25__section_gcd_14n_s2c"/>

## Structured Prompts

Structured prompts are the recommended way to define custom metrics. They use a predefined format that allows you to define the metrics.

> ### Sample Code:  
> ```
> {
>     "spec": {
>         "promptType": "structured",
>         "configuration": {
>             "modelConfiguration": {
>                 "name": "gpt-4",
>                 "version": "2024-02-15",
>                 #optional
>                 "parameters": [
>                     {
>                         "key": "maxlength",
>                         "value": "120000"
>                     }
>                 ]
>             },
>             "promptConfiguration": {
>                 "definition": "Measures how well the response aligns with verifiable facts",
>                 "evaluationTask": "Rate the factual accuracy of the response compared to the reference",
>                 "ratingRubric": [
>                     {
>                         "rating": 5,
>                         "rule": "Response is completely factual with no unsupported claims"
>                     },
>                     {
>                         "rating": 3,
>                         "rule": "Response has minor inaccuracies but no major contradictions"
>                     },
>                     {
>                         "rating": 1,
>                         "rule": "Response contains significant factual errors or hallucinations"
>                     }
>                 ],
>                 "criteria": "Evaluate based on facts, absence of hallucinations, and alignment with reference",
>                 "evaluationSteps": [
>                     "Compare response against reference material",
>                     "Identify any factual claims in the response",
>                     "Verify each claim against known facts",
>                     "Rate based on accuracy level"
>                 ],
>                 "examples": [
>                     {
>                         "prompt": "What is the capital of France?",
>                         "groundingInput": "Paris is the capital and most populous city of France.",
>                         "groundingOutput": "Paris is the capital and most populous city of France.",
>                         "response": "The capital of France is Paris.",
>                         "reference": "Paris is the capital and most populous city of France.",
>                         "rating": 5,
>                         "explanation": "Response is completely accurate and matches the reference"
>                     }
>                 ]
>             }
>         }
>     }
> }
> ```

-   **[Metric Management](metric-management-8a6292b.md "You can manage the lifecycle of your custom metrics, outside of your evaluation deployments.")**  
You can manage the lifecycle of your custom metrics, outside of your evaluation deployments.

