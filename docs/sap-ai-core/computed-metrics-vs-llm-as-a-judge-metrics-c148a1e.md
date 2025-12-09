<!-- loioc148a1e74e9b4704993d3ac63136369c -->

# Computed Metrics vs LLM-as-a-Judge Metrics

Computed metrics such as BERT Score, BLEU, and cosine similarity performed poorly compared to llm-as-a-judge metrics and were not selected for grounding evaluation.

Instead, we recommend these corresponding metrics:


<table>
<tr>
<th valign="top">

Computed Metric

</th>
<th valign="top">

LLM-as-a-Judge Metric

</th>
</tr>
<tr>
<td valign="top">

BERT Score with `user query` and `context` 

</td>
<td valign="top">

Pointwise RAG Context Relevance

</td>
</tr>
<tr>
<td valign="top">

BERT Score with `context` and `llm output` 

</td>
<td valign="top">

Pointwise RAG Groundedness

</td>
</tr>
</table>

