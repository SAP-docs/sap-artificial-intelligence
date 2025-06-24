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
    -   Generative AI hub not included

-   For region information, see [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?region=all&tab=feature&commercialModel=cpea).


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
    -   Generative AI hub not included

-   For region information, see [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?region=all&tab=feature&commercialModel=cpea).


For more information, see [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md) and [Metering and Pricing for SAP AI Core](metering-and-pricing-for-sap-ai-core-1e6cbac.md).

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

-   Includes the Standard plan, with the addition of generative AI capabilities in the generative AI hub.

-   Use of provided generative AI models is charged using adaptable pricing according to model choice, and the number of tokens sent and received.

-   For region information, see [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?region=all&tab=feature&commercialModel=cpea).


For more information, see [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md) and [Metering and Pricing for SAP AI Core](metering-and-pricing-for-sap-ai-core-1e6cbac.md).

</td>
<td valign="top">

Enterprise

</td>
</tr>
</table>



<a name="loioc7244c6a7e3b4ffc928a2564c216e7c7__section_w5l_cf2_1vb"/>

## Deployment Quotas

Each tenant is assigned a default quota that limits the number of deployments and replicas per deployment. If you reach this quota, your deployment will not be created and you will be notified accordingly. You can free up your quota by deleting existing deployments.

Alternatively, you can request an increase to your quota by creating a ticket on component `CA-ML-AIC`. Enter the description `Request to Increase Quota` and include details about the size of your increase, whether you want to include deployments, replicas, or both, and your subaccount ID.



<a name="loioc7244c6a7e3b4ffc928a2564c216e7c7__section_dyl_5kb_r1c"/>

## Resource Group Quotas

> ### Restriction:  
> The maximum number of resource groups is limited at tenant level to 50. If you reach this limit, you receive an error message. To free up space, delete some resource groups. Alternatively, raise a ticket to increase your quota.
> 
> For more information, see [Delete a Resource Group](delete-a-resource-group-40d83a2.md).



<a name="loioc7244c6a7e3b4ffc928a2564c216e7c7__section_ytk_tjz_ydc"/>

## Tenant-Wide Generic Secrets Quotas

Each tenant can have a maximum of five tenant-wide secrets. If you reach this limit, you receive an error message. To free up space, delete tenant-wide secrets as described at [Delete a Generic Secret](delete-a-generic-secret-d5d5187.md). Alternatively, submit a ticket to request an increase in your quota.

-   **[Free Tier](free-tier-4533adc.md "Enable the free tier option to get to know SAP AI Core with usage
		limits, to familiarize yourself with the service. Note that usage is limited with this option.")**  
Enable the free tier option to get to know SAP AI Core with usage limits, to familiarize yourself with the service. Note that usage is limited with this option.
-   **[Metering and Pricing for SAP AI Core](metering-and-pricing-for-sap-ai-core-1e6cbac.md "SAP AI Core
		provides a scalable infrastructure for AI model management, with usage-based pricing that
		lets you pay only for the resources you use.")**  
SAP AI Core provides a scalable infrastructure for AI model management, with usage-based pricing that lets you pay only for the resources you use.
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

