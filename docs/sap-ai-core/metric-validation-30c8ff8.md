<!-- loio30c8ff8e901945ba9475b93ef5bf7428 -->

# Metric Validation

Following are llm-as-a-judge metrics, which use another LLM to assess the response for specific criteria.





### Groundedness

Groundedness measures whether the response relies solely on the provided context documents and avoids introducing external information or unsupported claims. A response is considered fully grounded if all factual claims are verifiable against the provided context.

Groundedness depends on the user query, context, and LLM output.

> ### Note:  
> While the definition of groundedness only depends on context and LLM output, we found that giving the user query as additional background information increased the correlation score with the ground truth from 67% to 79%.



### Context Relevance

Context relevance measures how well the retrieved information from context documents matches the query.

Context relevance depends on the user query and context.



<a name="loio30c8ff8e901945ba9475b93ef5bf7428__section_djq_b2w_tfc"/>

## Validation Methodology

The above metrics were validated on the following datasets:

-   [Ragbench](https://huggingface.co/datasets/rungalileo/ragbench/viewer/covidqa/train?row=1&views%5B%5D=covidqa_train)
-   Two SAP internal datasets

Most datasets have ground truth scores, which were used to measure whether or not the metrics accurately captured performance. Ground truth scores are calculated based on a model's assessment of the ground truth data, and are verified by humans.

For datasets without ground truth scores, `gemini-2.5-pro` was used to generate synthetic scores, which were then verified by humans.

Tests for groundedness and context relevance using GPT-4o as a judge achieved a correlation of 79% and 83% with the ground truth scores, respectively.

Tests for groundedness and context relevance using GPT-4.1 as a judge achieved a correlation of 83.74% and 87.07% with the ground truth scores, respectively.

