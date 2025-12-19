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

BERTScore is a metric for evaluating the quality of text generation by comparing candidate text to reference text. It uses a pre-trained BERT model to generate contextual embeddings for each token, then measures similarity between these embeddings to assess how closely the candidate aligns with the references.

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

BLEU \(Bilingual Evaluation Understudy\) evaluates machine-translated text quality by calculating n-gram precision between candidate and reference translations. Scores range from 0 to 1, with higher values indicating greater similarity.

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

ROUGE \(Recall-Oriented Understudy for Gisting Evaluation\) is a set of metrics for evaluating summarization and machine translation by measuring overlap in n-grams, word sequences, and word pairs between generated and reference texts. This implementation is case-insensitive.

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

Validates an LLM-generated response against a predefined JSON Schema, returning a boolean indicating whether the response matches the schema.

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

Boolean indicating whether the input content filter was invoked.

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

Boolean indicating whether the output content filter was invoked.

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

Boolean indicating whether the output exactly matches the reference.

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

Indicates whether the output matches the expected language. Results may be inaccurate when the text is very short.

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

Evaluates the model’s ability to follow the instructions provided in the user prompt. Scores range from 1 to 5, with 1 indicating no fulfillment and 5 indicating complete fulfillment.

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

Evaluates whether an LLM response is correct, accurate, and factual using a user-provided reference, for both general and retrieval-augmented \(RAG\) use cases. Scores range from 1 to 5, with 1 indicating completely incorrect and 5 indicating fully correct

</td>
<td valign="top">

No

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

Measures how closely the model’s response relates to the user prompt, for both general and RAG use cases. Scores range from 1 to 5, with higher values indicating greater relevance.

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

Measures how short and concise the model’s response is. Scores range from 1 to 5, with higher values indicating a more concise answer.

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

Evaluates whether the model’s response is supported by the provided context, measuring factual consistency in RAG use cases. Scores range from 1 to 3, with higher values indicating stronger grounding in the context.

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

Evaluates how relevant the retrieved context is to the user prompt, indicating the quality of the context retrieval stage in RAG systems. Scores range from 1 to 3, with higher values indicating that the context directly addresses the user prompt.

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

Measures how much of the provided context is relevant and useful relative to the user prompt. Scores range from 1 to 3, with higher values indicating a greater proportion of relevant context.

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

Evaluates how effectively the model’s response incorporates all relevant information from the provided context that is necessary to fully address the user prompt. Scores range from 1 to 5, with higher values indicating minimal relevant omissions.

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

