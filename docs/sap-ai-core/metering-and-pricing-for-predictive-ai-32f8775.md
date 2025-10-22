<!-- loio32f87752baed40368f49d38e49a09a2f -->

# Metering and Pricing for Predictive AI



<a name="loio32f87752baed40368f49d38e49a09a2f__section_jm4_zb4_jfc"/>

## Metering for Predictive AI

Custom AI workloads involve diverse resource types, each with varying performance and efficiency levels. Measuring key resources like compute power, storage, and baseline costs is crucial. Non-billable units of measure \(UoM\) are used to represent the consumption of these resources.

or example, compute-heavy AI models on high-performance instances consume more resources per hour than smaller, less demanding workloads. This results in proportionally higher costs. Pricing reflects true resource consumption.

Custom AI development requirements vary significantly based on the use case. A range of compute infrastructure resources is available, differing in CPU cores, memory \(GB\), and GPU presence for GPU-powered workloads like model training. Available resources are shown in the table.

> ### Note:  
> Infrastructure specifications depend on the chosen hyperscaler. For more information, see [Choose an Instance](choose-an-instance-57f4f19.md).


<table>
<tr>
<th valign="top">

Resource Type

</th>
<th valign="top">

SAP AI Core Resources

</th>
<th valign="top">

Unit of Measure \(UoM\)

</th>
</tr>
<tr>
<td valign="top" rowspan="7">

Compute

</td>
<td valign="top">

Starter Instance \(min. 2.5 GB, 1 CPU core\)

</td>
<td valign="top" rowspan="7">

Node hour

</td>
</tr>
<tr>
<td valign="top">

Basic Instance \(min. 10 GB, 3 CPU cores\)

</td>
</tr>
<tr>
<td valign="top">

Basic.8x Instance \(min. 115 GB, 31 CPU cores\)

</td>
</tr>
<tr>
<td valign="top">

Infer-S Instance \(min. 10 GB, 3 CPU cores, standard GPU\)

</td>
</tr>
<tr>
<td valign="top">

Infer-M Instance \(min. 25 GB, 7 CPU cores, standard GPU\)

</td>
</tr>
<tr>
<td valign="top">

Infer-L Instance \(min. 55 GB, 15 CPU cores, standard GPU\)

</td>
</tr>
<tr>
<td valign="top">

Train-L Instance \(min. 47 GB, 5 CPU cores, advanced GPU\)

</td>
</tr>
<tr>
<td valign="top">

Storage

</td>
<td valign="top">

Standard SSD Volume

</td>
<td valign="top">

Gigabyte hour

</td>
</tr>
<tr>
<td valign="top">

Baseline

</td>
<td valign="top">

Fixed cluster resources \(instances, storage, SAP HANA, Kubernetes, DevOps, support, and so on\)

</td>
<td valign="top">

Tenant hour

</td>
</tr>
</table>

Custom AI models can incur compute, storage, and baseline costs. You have the flexibility to select the components that best suit your needs. If you use compute or storage resources, the system automatically applies baseline charges every hour, up to a maximum of 730 hours.

> ### Note:  
> You can process data in parallel by using multiple nodes. Costs are calculated in node hours. For example, processing data for 1 hour on 2 nodes equals 2 node hours. However, it incurs only 1 hour of baseline costs.



<a name="loio32f87752baed40368f49d38e49a09a2f__section_sr2_qkl_kfc"/>

## Pricing for Predictive AI

The billing metric for SAP BTP is referred to as “capacity units”. Capacity units are calculated using conversion factors applied to compute, storage, and baseline intermediary UoM values. This allows you to calculate a specific price for the infrastructure used based on your compute and storage requirements.

Here's an example calculation, using fictitious values:

> ### Example:  
> Training a small model on a GPU node and serving it on a CPU node later in the same month results in the following costs:
> 
> -   Baseline: Total node hours of compute instances across the full month
> -   Storage: Temporary high-speed storage \(for example, SSD\) used during training and inference to stream or copy data
> -   Compute: Compute consumption based on node hours and chosen compute instances across the full month
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Resource Type
> 
> </th>
> <th valign="top">
> 
> Unit of Measure
> 
> </th>
> <th valign="top">
> 
> Capacity Unit \(CU\) Value
> 
> </th>
> <th valign="top">
> 
> Fictional Usage
> 
> </th>
> <th valign="top">
> 
> Conversion to CU
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> Compute
> 
> </td>
> <td valign="top">
> 
> node hour
> 
> </td>
> <td valign="top">
> 
> 0.3900
> 
> </td>
> <td valign="top">
> 
> 300 node hours in Basic Instance
> 
> </td>
> <td valign="top">
> 
> 300 \* 0.39 = 117 CU
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Compute
> 
> </td>
> <td valign="top">
> 
> node hour
> 
> </td>
> <td valign="top">
> 
> 1.552
> 
> </td>
> <td valign="top">
> 
> 100 node hours in Infer-M Instance
> 
> </td>
> <td valign="top">
> 
> 100 \* 1.552 = 155.2 CU
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Storage
> 
> </td>
> <td valign="top">
> 
> gigabyte hour
> 
> </td>
> <td valign="top">
> 
> 0.0003
> 
> </td>
> <td valign="top">
> 
> 10.000 gigabyte hours
> 
> </td>
> <td valign="top">
> 
> 0.0003\*5,000 = 1.5 CU
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Baseline
> 
> </td>
> <td valign="top">
> 
> tenant hour
> 
> </td>
> <td valign="top">
> 
> 1.2241
> 
> </td>
> <td valign="top">
> 
> 400 baseline tenant hours
> 
> </td>
> <td valign="top">
> 
> 1.2241\*400 = 489.64 CUs
> 
> </td>
> </tr>
> </table>

Infrastructure specifications are combined minimum values; actual numbers vary by deployed hyperscaler and may be higher.

The CUs can be converted to monetary values in the BTP Discovery Center Estimator. For more information, see [BTP Discovery Center Estimator](https://discovery-center.cloud.sap/estimator/?commercialModel=btpea).

> ### Recommendation:  
> For an estimate of projected costs, use the [SAP AI Core Cost Calculator](https://ai-core-calculator.cfapps.eu10.hana.ondemand.com/uimodule/index.html).



## Typical Consumption Patterns

Depending on your infrastructure and your consumption pattern \(S, M or L\), you need on average the following node hours for compute, storage, and baseline hours.


<table>
<tr>
<th valign="top">

T Shirt Size

</th>
<th valign="top">

Starter

</th>
<th valign="top">

Basic

</th>
<th valign="top">

Basic8x

</th>
<th valign="top">

Infer.S

</th>
<th valign="top">

Infer.M

</th>
<th valign="top">

Infer.L

</th>
<th valign="top">

Train.L

</th>
<th valign="top">

Storage

</th>
<th valign="top">

Baseline

</th>
</tr>
<tr>
<td valign="top">

S

</td>
<td valign="top">

50

</td>
<td valign="top">

30

</td>
<td valign="top">

0

</td>
<td valign="top">

300

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

50

</td>
<td valign="top">

0

</td>
<td valign="top">

430

</td>
</tr>
<tr>
<td valign="top">

M

</td>
<td valign="top">

0

</td>
<td valign="top">

900

</td>
<td valign="top">

0

</td>
<td valign="top">

160

</td>
<td valign="top">

1880

</td>
<td valign="top">

1440

</td>
<td valign="top">

120

</td>
<td valign="top">

0

</td>
<td valign="top">

730

</td>
</tr>
<tr>
<td valign="top">

L

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

800

</td>
<td valign="top">

10000

</td>
<td valign="top">

0

</td>
<td valign="top">

2300

</td>
<td valign="top">

0

</td>
<td valign="top">

730

</td>
</tr>
</table>

