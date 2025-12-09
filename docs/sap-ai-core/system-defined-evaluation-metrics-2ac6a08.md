<!-- loio2ac6a0896b474fe8b6ba614a7b724d58 -->

# System-Defined Evaluation Metrics



System defined metrics are available when using the `genai-evaluation` global scenario.

The following types of metrics are supported:

-   Computed
-   LLM-as-a-judge



## Computed Metrics

The following system-defined computed metrics are supported, depending on whether you use the simplified or standard evaluation workflow:


<table>
<tr>
<th valign="top">

Metric Used in Simplified Workflow

</th>
<th valign="top">

Metric Used in Standard Workflow

</th>
<th valign="top">

Description

</th>
<th valign="top">

Reference Required

</th>
</tr>
<tr>
<td valign="top">

`BERT Score` 

</td>
<td valign="top">

`bert_score` 

</td>
<td valign="top">

Uses pretrained embeddings and cosine similarity to incorporate semantic similarity where two tokens aren't an exact match. Returns precision, recall, and F1 measure.

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

`BLEU` 

</td>
<td valign="top">

`bleu` 

</td>
<td valign="top">

Compares a translated text to a ground truth reference using n-grams, with a focus on precision.

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

`ROUGE` 

</td>
<td valign="top">

`rouge` 

</td>
<td valign="top">

Compares a translated or summarized text to a ground truth reference using n-grams, with a focus on recall.

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

`JSON Schema Match` 

</td>
<td valign="top">

`json_schema_match` 

</td>
<td valign="top">

Validates LLM-generated responses against a predefined JSON schema, returns Boolean result.

For more information, see [JSON Schema Match](json-schema-match-57d88de.md).

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Content Filter on Input` 

</td>
<td valign="top">

`content_filter_on_input` 

</td>
<td valign="top">

Records whether orchestration input was rejected by the input filter.

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Content Filter on Output` 

</td>
<td valign="top">

`content_filter_on_output` 

</td>
<td valign="top">

Records whether orchestration input was rejected by the output filter

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Exact Match` 

</td>
<td valign="top">

`exact_match` 

</td>
<td valign="top">

Records whether the output exactly matches the reference.

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

`Language Match` 

</td>
<td valign="top">

`language_match` 

</td>
<td valign="top">

Returns `true` or `false` to indicate if the text matches the given language.

For more information, see [Language Match](language-match-c74df7d.md).

</td>
<td valign="top">

No

</td>
</tr>
</table>



## LLM-as-a-Judge Metrics

The following system-defined LLM-as-a-judge metrics are supported, depending on whether you use the simplified or standard evaluation workflow:


<table>
<tr>
<th valign="top">

Metric Used in Simplified Workflow

</th>
<th valign="top">

Metric Used in Standard Workflow

</th>
<th valign="top">

Description

</th>
<th valign="top">

Reference Required

</th>
</tr>
<tr>
<td valign="top">

`Pointwise Instruction Following` 

</td>
<td valign="top">

`pointwise_instruction_following` 

</td>
<td valign="top">

Assesses the model's ability to follow instructions provided in the user prompt.

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Pointwise Correctness` 

</td>
<td valign="top">

`pointwise_correctness` 

</td>
<td valign="top">

Evaluates whether an LLM response is correct, accurate, and factual, for both general and retrieval-augmented \(RAG\) use cases.

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

`Pointwise Answer Relevance` 

</td>
<td valign="top">

`pointwise_answer_relevance` 

</td>
<td valign="top">

Assesses whether the model's response is related to user prompt, for both general and retrieval-augmented \(RAG\) use cases.

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Pointwise Conciseness` 

</td>
<td valign="top">

`pointwise_conciseness` 

</td>
<td valign="top">

Assesses whether the model's response is a short and concise answer to user prompt.

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Pointwise RAG Groundedness` 

</td>
<td valign="top">

`pointwise_rag_groundedness` 

</td>
<td valign="top">

Evaluates if the LLM response is supported by the provided context, measuring factual consistency for retrieval-augmented \(RAG\) use cases.

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Pointwise RAG Context Relevance` 

</td>
<td valign="top">

`pointwise_rag_context_relevance` 

</td>
<td valign="top">

Evaluates how relevant the retrieved context is to the user query, indicating the quality of the context retrieval stage in RAG systems.

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Pointwise RAG Context Precision`\*

</td>
<td valign="top">

`pointwise_rag_context_precision` 

</td>
<td valign="top">

Measures how much of the provided context is relevant and useful compared to user query.

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`Pointwise RAG Completeness`\*

</td>
<td valign="top">

`pointwise_rag_completeness` 

</td>
<td valign="top">

Evaluates how effectively the response incorporates all relevant information from the provided context that’s necessary to fully address the user query.

</td>
<td valign="top">

No

</td>
</tr>
</table>

Entries marked with an asterisk \(\*\) are experimental metrics.

-   **[Language Match](language-match-c74df7d.md "")**  

-   **[JSON Schema Match](json-schema-match-57d88de.md "")**  

-   **[Grounding Metrics](grounding-metrics-1b76521.md "")**  


**Related Information**  


[Evaluations](evaluations-14699b0.md "")

