<!-- loio61750086c8ad4c9091008a2f4d056992 -->

# Cron Expressions



You can schedule updates to your pipeline, at intervals of your choice by adding a `cronExpression` when you create your pipeline.

Cron expressions have 5 fields denoted by a string pf asterisks. The values for these fields are as follows:

**Pipeline Scheduling: Fields and Values**


<table>
<tr>
<th valign="top">

\*

</th>
<th valign="top">

\*

</th>
<th valign="top">

\*

</th>
<th valign="top">

\*

</th>
<th valign="top">

\*

</th>
</tr>
<tr>
<td valign="top">

Minute \(0–59\)

</td>
<td valign="top">

Hour \(0–23\)

</td>
<td valign="top">

Day of the month \(1–31\)

</td>
<td valign="top">

Month \(1–12\)

</td>
<td valign="top">

Day of the week \(0–6\)

</td>
</tr>
</table>

The minimum value supported in the pipeline API is 1 hour.

**Pipeline Scheduling Fields: Example Values**


<table>
<tr>
<th valign="top">

Expression

</th>
<th valign="top">

Schedule

</th>
</tr>
<tr>
<td valign="top">

0\*\*\*\*

</td>
<td valign="top">

Every hour

</td>
</tr>
<tr>
<td valign="top">

00\*\*\*

</td>
<td valign="top">

Every day at 12:00 a.m.

</td>
</tr>
<tr>
<td valign="top">

00\*\*FRI

</td>
<td valign="top">

At 12:00 a.m. only on Friday

</td>
</tr>
<tr>
<td valign="top">

001\*\*

</td>
<td valign="top">

At 12:00 a.m. on the first day of the month

</td>
</tr>
</table>

> ### Note:  
> Each repetition of your pipeline is a new deployment, and incurs costs.

