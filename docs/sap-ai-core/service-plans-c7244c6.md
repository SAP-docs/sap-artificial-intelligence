<!-- loioc7244c6a7e3b4ffc928a2564c216e7c7 -->

# Service Plans

The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.

Your use case will determine whether you choose a free tier option for SAP AI Core or a paid service plan.

The following service plans are available:

-   Free

-   Standard



<table>
<tr>
<th valign="top">

Service Plan



</th>
<th valign="top">

Details



</th>
<th valign="top">

Account Type



</th>
</tr>
<tr>
<td valign="top">

Free



</td>
<td valign="top">

-   Used for trial and testing purposes.

-   Only community support is available for free tier service plans and these are not subject to SLAs.

-   Limitations:
    -   Limited to one instance per Global account
    -   Limited to one execution or deployment running at any given time
    -   Limited to the default resource group
    -   Limited to the Starter AI Core resource plan
    -   Limited to active instance\(s\) of either free or standard plan \(mutually exclusive\) within a subaccount

-   Region

    -   **AWS**: Europe \(Frankfurt\)

    -   **AWS**: Europe \(Frankfurt\) EU Access

    -   **AWS**: Japan \(Tokyo\)

    -   **AWS**: U.S. East \(VA\)



> ### Note:  
> Customers can create one SAP AI Core free plan instance, if and only if there are no active standard plan instances within the subaccount. Tenants can update their plan from free to standard, but not from standard to free. A standard plan SAP AI Core instance cannot be created if there is an active free plan instance in the subaccount.

For more information, see [Free Tier](free-tier-4533adc.md), the Starter plan in [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md) and [Using Free Service Plans](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/524e1081d8dc4b0f9d055a6bec383ec3.html?q=using%20free%20service%20plans).



</td>
<td valign="top">

Enterprise



</td>
</tr>
<tr>
<td valign="top">

Standard



</td>
<td valign="top">

-   SAP AI Core default service plan.

-   Service plan intended for productive usage.

-   A fixed price is charged each month for every subaccount \(tenant\).

-   Use of resources is charged using adaptable pricing according to the resource type used.

-   Limitations:
    -   An SAP AI Core standard plan instance cannot be created if there is an active free plan instance

-   Region

    -   **AWS**: Europe \(Frankfurt\)

    -   **AWS**: Europe \(Frankfurt\) EU Access

    -   **AWS**: Japan \(Tokyo\)

    -   **AWS**: U.S. East \(VA\)



For more information, see [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md) and [Metering and Pricing](metering-and-pricing-b5c7215.md).



</td>
<td valign="top">

Enterprise



</td>
</tr>
</table>



<a name="loioc7244c6a7e3b4ffc928a2564c216e7c7__section_w5l_cf2_1vb"/>

## Deployment Quotas

Each tenant is assigned a default quota that limits the number of deployments and replicas per deployment. If you reach this quota, your deployment will not be created, and you will be notified. You can free up your quota by deleting existing deployments.

Alternatively, you can request a quota increase by creating a ticket. The `component` name is ***CA-ML-AIC*** and ticket title is ***Request to Increase Quota***. Please include details about the size of your increase, if you want to include deployments, replicas or both, and your subaccount ID.

-   **[Free Tier](free-tier-4533adc.md "The free tier service plan allows one instance of SAP AI Core that
		lets you explore the available features and capabilities without cost.")**  
The free tier service plan allows one instance of SAP AI Core that lets you explore the available features and capabilities without cost.
-   **[Metering and Pricing](metering-and-pricing-b5c7215.md "SAP AI Core is metered based on various nonbillable units of measure
		(UoM), depending on which resources of SAP AI Core are
		consumed.")**  
SAP AI Core is metered based on various nonbillable units of measure \(UoM\), depending on which resources of SAP AI Core are consumed.
-   **[Choose a Resource Plan](choose-a-resource-plan-3a06d84.md "You can configure SAP AI Core to use different infrastructure
		resources for
		different
		tasks, based on task demand.
		SAP AI Core provides several preconfigured infrastructure bundles called
			“resource plans” for this purpose. ")**  
You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.
-   **[Update from Free Tier to Standard Plan](update-from-free-tier-to-standard-plan-924f892.md "Learn how to update to the SAP AI Core standard plan, after
		exploring the product in Free Tier.")**  
Learn how to update to the SAP AI Core standard plan, after exploring the product in Free Tier.

**Related Information**  


[Free Tier](free-tier-4533adc.md "The free tier service plan allows one instance of SAP AI Core that lets you explore the available features and capabilities without cost.")

[SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?service_plan=standard&region=europe(frankfurt)&tab=service_plan)

[SAP BTP Service Description Guide](https://www.sap.com/about/agreements/policies/cloud-platform.html)

[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

