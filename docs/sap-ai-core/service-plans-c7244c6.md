<!-- loioc7244c6a7e3b4ffc928a2564c216e7c7 -->

# Service Plans

The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.

Your use case will determine whether you choose a free tier option for SAP AI Core or a paid service plan.

The following service plans are available:

-   Free

-   Standard

-   Extended


> ### Restriction:  
> SAP AI Core free tier is only available in SAP BTP free tier, not SAP BTP trial.


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

-   Get to know SAP AI Core using a free service, with limitations.
-   Only community support is available for free tier service plans and these are not subject to SLAs.

-   Limitations:
    -   Limited to one instance per Global account
    -   Limited to one execution or deployment running at any given time
    -   Limited to the default resource group
    -   Limited to the Starter AI Core resource plan
    -   Limited to active instance\(s\) of either free or standard plan \(mutually exclusive\) within a subaccount
    -   Generative AI Hub not included

-   For region information, see [SAP Discovery Centre](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?region=all&tab=feature&commercialModel=cpea).


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

-   Service plan intended for productive usage.

-   Use of resources for custom workloads is charged using adaptable pricing according to the resource type used, with the addition of a baseline charge for service use.

-   Limitations:
    -   An SAP AI Core standard plan instance cannot be created if there is an active free plan instance
    -   Generative AI Hub not included

-   For region information, see [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?region=all&tab=feature&commercialModel=cpea).


For more information, see [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md) and [Metering and Pricing for SAP AI Core](metering-and-pricing-for-sap-ai-core-b5c7215.md).

</td>
<td valign="top">

Enterprise

</td>
</tr>
<tr>
<td valign="top">

Extended

</td>
<td valign="top">

-   Includes the Standard plan, with the addition of generative AI capabilities in the Generative AI Hub.

-   Use of provided generative AI models is charged using adaptable pricing according to model choice, and the number of tokens sent and received.

-   For region information, see [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?region=all&tab=feature&commercialModel=cpea).


For more information, see [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md), [Resource Plans for Large Language Models](https://help.sap.com/viewer/e2eb894cbc6445f99784ccd973d2ddee/CLOUD/en-US/ecb5477a45044b64aa860dbd872d97a3.html "You can configure SAP AI Core to use different infrastructure resources for different tasks. SAP AI Core provides several preconfigured infrastructure bundles called "resource plans" for this purpose.") :arrow_upper_right: and [Metering and Pricing for SAP AI Core](metering-and-pricing-for-sap-ai-core-b5c7215.md).

</td>
<td valign="top">

Enterprise

</td>
</tr>
</table>



<a name="loioc7244c6a7e3b4ffc928a2564c216e7c7__section_w5l_cf2_1vb"/>

## Deployment Quotas

Each tenant is assigned a default quota that limits the number of deployments and replicas per deployment. If you reach this quota, your deployment will not be created, and you will be notified. You can free up your quota by deleting existing deployments.

Alternatively, you can request a quota increase by creating a ticket. The `component` name is `CA-ML-AIC` and ticket title is `Request to Increase Quota`. Please include details about the size of your increase, if you want to include deployments, replicas or both, and your subaccount ID.

-   **[Free Tier](free-tier-4533adc.md "Enable the free tier option to get to know SAP AI Core with usage
		limits, to familiarize yourself with the service. Note that usage is limited with this option.")**  
Enable the free tier option to get to know SAP AI Core with usage limits, to familiarize yourself with the service. Note that usage is limited with this option.
-   **[Metering and Pricing for SAP AI Core](metering-and-pricing-for-sap-ai-core-b5c7215.md "SAP AI Core is metered based on various nonbillable units of measure
		(UoM), depending on which resources of SAP AI Core are
		consumed.")**  
SAP AI Core is metered based on various nonbillable units of measure \(UoM\), depending on which resources of SAP AI Core are consumed.
-   **[Metering and Pricing for the Generative AI Hub](metering-and-pricing-for-the-generative-ai-hub-a5212f3.md "The use of large language models (LLMs) in the generative AI hub is metered using
			GenAI tokens and capacity units.")**  
The use of large language models \(LLMs\) in the generative AI hub is metered using GenAI tokensand capacity units.
-   **[Choose a Resource Plan](choose-a-resource-plan-c58d4e5.md "You can configure SAP AI Core to use different infrastructure
		resources for
		different
		tasks, based on demand.
		SAP AI Core provides several preconfigured infrastructure bundles called
			“resource plans” for this purpose.")**  
You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.
-   **[Update a Service Plan](update-a-service-plan-924f892.md "Learn how to update to the SAP AI Core standard or extended plan,
		after exploring the product in Free Tier.")**  
Learn how to update to the SAP AI Core standard or extended plan, after exploring the product in Free Tier.

**Related Information**  


[Free Tier](free-tier-4533adc.md "Enable the free tier option to get to know SAP AI Core with usage limits, to familiarize yourself with the service. Note that usage is limited with this option.")

[SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?service_plan=standard&region=europe(frankfurt)&tab=service_plan)

[SAP BTP Service Description Guide](https://www.sap.com/about/agreements/policies/cloud-platform.html)

[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

