<!-- loio56727a392781470e926145571edcaf9f -->

# Variable Mapping

Variable mapping enables you to align variable names between orchestration configurations, metric evaluators, and test datasets, ensuring correct data flow even when attribute names differ. Use this feature to resolve naming mismatches and maintain consistency in automated testing and evaluation workflows.

Variable mappings map properties in the orchestration configuration or response and metric evaluators to attributes in the test data set. By default, variable names in the prompt templates are matched against the attribute names in the test dataset. Where variable names and test data attribute names are mismatched, mapping is required. For example, the prompt template in your orchestration configuration contains an attribute called “query” containing your prompt message, whereas the corresponding attribute in your ground truth dataset is called “questions”. In this case, you have to map the orchestration configuration variable “query” to the dataset variable “questions”.

Variable mappings are provided as a JSON dictionary in the following format:

> ### Sample Code:  
> ```
> {
>   "target_prefix/field_name": "source_prefix/field_name"
> }
> ```



<a name="loio56727a392781470e926145571edcaf9f__section_ycj_kpn_s2c"/>

## Case 1

Mapping a variable in the orchestration workflows to an attribute in the test dataset

In the following example, “prompt” and “data” are target and source prefixes for the orchestration workflow prompt template and the test dataset respectively and “query” and “question” are the name mismatched prompt template variable and dataset attribute.

> ### Sample Code:  
> ```
> {
>   "prompt/query": "data/question"
> }
> ```



<a name="loio56727a392781470e926145571edcaf9f__section_trn_mpn_s2c"/>

## Case 2

Mapping a variable of a metric evaluator to an attribute in the test dataset.

For variables that are commonly used in judge prompts, the following system-defined variable names are defined, and their values are populated automatically.


<table>
<tr>
<th valign="top">

Variable Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

aicore\_llm\_prompt

</td>
<td valign="top">

The prompt sent to the LLM

</td>
</tr>
<tr>
<td valign="top">

aicore\_llm\_completion

</td>
<td valign="top">

The completion string returned by the LLM

</td>
</tr>
</table>

You must define the following common values for variables.


<table>
<tr>
<th valign="top">

Variable Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

reference

</td>
<td valign="top">

The ground truth reference string provided by the user.

</td>
</tr>
</table>

The variable names starting with "aicore" are reserved and must not be used for other variables or dataset attributes.

In the following example, the target prefix is the ID of the metric evaluator and the source prefix is “data”.

> ### Sample Code:  
> ```
> {
>   ...
>   "<metric_id>/reference": "data/ground_truth"
>   ...
> }
> ```

To map a dataset attribute to a variable being used in all metric evaluators, the target prefix `all_metrics` can be used as the target prefix. For example:

> ### Sample Code:  
> ```
> {
>   ...
>   "all_metrics/reference": "data/ground_truth"
>   ...
> }
> ```

