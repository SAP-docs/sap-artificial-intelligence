<!-- loioaa46126be8f94e35b6d81125ffb73960 -->

# View Evaluation Results



<a name="loioaa46126be8f94e35b6d81125ffb73960__prereq_vv3_mvn_s2c"/>

## Prerequisites

You have successfully run an evaluation execution. For more information, see [Create an Evaluation \(Simplified\)](create-an-evaluation-77ebfe5.md).



<a name="loioaa46126be8f94e35b6d81125ffb73960__context_spm_gtt_52c"/>

## Context

The evaluation job will calculate and report the aggregate job statistics for each completion.

Aggregate job statistics include the following:


<table>
<tr>
<th valign="top">

Statistic

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

average\_latency

</td>
<td valign="top">

The average time taken in seconds to get a completion from the orchestration service

</td>
</tr>
<tr>
<td valign="top">

completion\_count

</td>
<td valign="top">

Number of completions evaluated

</td>
</tr>
<tr>
<td valign="top">

total\_prompt\_tokens

</td>
<td valign="top">

Sum of prompt\_tokens of completions

</td>
</tr>
<tr>
<td valign="top">

total\_completion\_tokens

</td>
<td valign="top">

Sum of completion\_tokens of completions

</td>
</tr>
</table>

The following aggregate result statistics are included for all metrics:


<table>
<tr>
<th valign="top">

Statistic

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

mean

</td>
<td valign="top">

The center point of a collection of values, also known as arithmitic mean

</td>
</tr>
<tr>
<td valign="top">

stddev

</td>
<td valign="top">

The amount of deviation from the mean

</td>
</tr>
<tr>
<td valign="top">

median

</td>
<td valign="top">

The middle value or 50th percentile of a collection of values

</td>
</tr>
<tr>
<td valign="top">

p90

</td>
<td valign="top">

The value at the 90th percentile of a collection of values

</td>
</tr>
<tr>
<td valign="top">

p95

</td>
<td valign="top">

The value at the 95th percentile of a collection of values

</td>
</tr>
</table>

In addition, `BERT Score` includes these statistics for the sub metrics F1, precision, and recall.

**Recall** is the fraction of correctly labelled positive instances, in the context of all available positive instances. It can be computed using the equation: Recall = TP/\(TP + FN\), where TP is the number of true positives and FN is the number of false negatives.

**Precision** is the fraction of correctly labeled positive instances, in the context of all positively labelled instances. It is computed using the equation: Precision = TP/\(TP + FP\), where TP is the number of true positives and FP is the number of false positives.

The **F1 score** is the harmonic mean of the precision and recall. It can be computed with the equation: F1 = 2 \(precision\*recall\)/\(precision + recall\)



## Procedure

Retrieve your results by sending a GET request to one of the following endpoints:

-   Using your `executionId`: `{{apiurl}}/v2/lm/metrics?tagFilters=evaluation.ai.sap.com/child-of={execution_id}`
-   Using your `runName`: `{{apiurl}}/v2/lm/metrics?tagFilters=evaluation.ai.sap.com/run-name={run_name}`

 > ### Note:  
> After and evaluation is complete, there may be residual output artifacts such as logs or instance level metrics, that can be safely deleted by users.

 