<!-- loiob5c721567f4540a3a1f34376a449cce5 -->

# Metering and Pricing

SAP AI Core is metered based on various nonbillable units of measure \(UoM\), depending on which resources of SAP AI Core are consumed.

The following resources and nonbillable UoMs are available:


<table>
<tr>
<th valign="top">

Resource Type



</th>
<th valign="top">

Infrastructure Resource



</th>
<th valign="top">

Unit of Measure



</th>
</tr>
<tr>
<td valign="top" rowspan="7">

Compute



</td>
<td valign="top">

Starter Instance



</td>
<td valign="top" rowspan="7">

Node hour



</td>
</tr>
<tr>
<td valign="top">

Basic Instance



</td>
</tr>
<tr>
<td valign="top">

Basic.8x Instance



</td>
</tr>
<tr>
<td valign="top">

Infer-S Instance



</td>
</tr>
<tr>
<td valign="top">

Infer-M Instance



</td>
</tr>
<tr>
<td valign="top">

Infer-L Instance



</td>
</tr>
<tr>
<td valign="top">

Train-L Instance



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

gigabyte hour



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

> ### Note:  
> Infrastructure specifications depend on the chosen hyperscaler. For more information, see [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md).
> 
> Each metered record is translated to the billable metric “capacity units”. Every resource has a specific conversion rate for translating the UoM to capacity units. For the applicable conversion rates, see the [SAP BTP Service Description Guide](https://www.sap.com/about/agreements/policies/cloud-platform.html).

All “Compute” and “Storage” resource consumption is based on the actual metered usage.

Baseline charges are automatically calculated based on the following: For each active tenant hour where one of the “Compute” or “Storage” resources is being consumed within a tenant, one “Baseline” tenant hour is automatically charged. If multiple resources are used within the same hour, only one “Baseline” tenant hour will be charged.

> ### Example:  
> This example uses fictitious values. For the current conversion rates, see the [SAP BTP Service Description Guide](https://www.sap.com/about/agreements/policies/cloud-platform.html).
> 
> Let's assume the following parameters:
> 
> -   1 node hour of a Starter Instance equals 0.5 capacity units.
> 
> -   1 node hour of an Infer-M Instance equals 2 capacity units.
> 
> -   1 tenant hour of Baseline equals 1.5 capacity units.
> 
> -   1 capacity unit costs EUR 1
> 
> 
> If you consume 100 hours of a Starter Instance and 300 hours of an Infer-M Instance, and you are active on the cluster for 300 hours in a month, the following costs will accrue:
> 
> -   100 node hours of Starter Instance = 100 \* 0.5 capacity units = 50 capacity units
> -   300 node hours of Infer-M Instance = 300 \* 2 capacity units = 600 capacity units
> -   300 tenant hours of Baseline = 300 \* 1.5 capacity units = 450 capacity units
> -   **Total = 1,100 capacity units = EUR 1,100**

> ### Note:  
> It is possible to process data in parallel, using more than one node. Costs are calculated in node hours, meaning that 1 hour of data processing, on 2 nodes is equal to 2 node hours.

> ### Recommendation:  
> For an estimate of projected costs, use the [SAP AI Core Cost Calculator](https://ai-core-calculator.cfapps.eu10.hana.ondemand.com/uimodule/index.html).

**Related Information**  


[SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?service_plan=standard&region=europe(frankfurt)&tab=service_plan)

[SAP BTP Service Description Guide](https://www.sap.com/about/agreements/policies/cloud-platform.html)

[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

