<!-- loioc7244c6a7e3b4ffc928a2564c216e7c7 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Service Plans

The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.

Your choice depends on your use case:

-   Use the *Free* plan to explore the service with limited resources and community-only support.

-   Use the *Standard* plan for production workloads without generative AI.

-   Use the *Extended* plan for production workloads with generative AI hub access.




<a name="loioc7244c6a7e3b4ffc928a2564c216e7c7__section_afd_psm_lgc"/>

## Comparison of Service Plans


<table>
<tr>
<th valign="top">

Feature / Plan

</th>
<th valign="top">

Free \(Exploration\)

</th>
<th valign="top">

Standard \(Production\)

</th>
<th valign="top">

Extended \(Production + Generative AI\)

</th>
</tr>
<tr>
<td valign="top">

Account type

</td>
<td valign="top">

Enterprise account \(SAP BTP free tier only; not available in SAP BTP trial\)

</td>
<td valign="top">

Enterprise account

</td>
<td valign="top">

Enterprise account

</td>
</tr>
<tr>
<td valign="top">

Support

</td>
<td valign="top">

Community support only \(no SLA\)

</td>
<td valign="top">

Full SAP support with SLA

</td>
<td valign="top">

Full SAP support with SLA

</td>
</tr>
<tr>
<td valign="top">

Generative AI hub

</td>
<td valign="top">

<span style="color:#cc1919;"><span class="SAP-icons-V5"></span></span> Not included

</td>
<td valign="top">

<span style="color:#cc1919;"><span class="SAP-icons-V5"></span></span> Not included

</td>
<td valign="top">

<span style="color:#007833;"><span class="SAP-icons-V5"></span></span> Included

</td>
</tr>
<tr>
<td valign="top">

Pricing

</td>
<td valign="top">

Free

</td>
<td valign="top">

Pay per resource + baseline charge

</td>
<td valign="top">

Pay per resource + model/token usage

</td>
</tr>
<tr>
<td valign="top">

Instances per subaccount

</td>
<td valign="top">

1 instance \(mutually exclusive with Standard\)

</td>
<td valign="top">

1+ instances \(mutually exclusive with Free\)

</td>
<td valign="top">

1+ instances

</td>
</tr>
<tr>
<td valign="top">

Executions/Deployments

</td>
<td valign="top">

1 running execution or deployment at a time

</td>
<td valign="top">

Multiple

</td>
<td valign="top">

Multiple

</td>
</tr>
<tr>
<td valign="top">

Resource groups

</td>
<td valign="top">

Default group only

</td>
<td valign="top">

Multiple \(quota applies\)

</td>
<td valign="top">

Multiple \(quota applies\)

</td>
</tr>
<tr>
<td valign="top">

Resource plan

</td>
<td valign="top">

Starter plan only

</td>
<td valign="top">

Choice of resource plans

</td>
<td valign="top">

Choice of resource plans

</td>
</tr>
<tr>
<td valign="top">

Upgrade/downgrade rules

</td>
<td valign="top">

Upgrade from Free to Standard is possible.

Downgrade from Standard to Free is not possible.

</td>
<td valign="top">

Cannot be created if a Free plan is active in the same subaccount.

</td>
<td valign="top">

Cannot be created if a Free plan is active in the same subaccount.

</td>
</tr>
</table>

> ### Note:  
> You can only run either a Free or a Standard plan in the same subaccount — not both. Extended follows the same rules as Standard.

For supported regions, see [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?region=all&tab=feature&commercialModel=cpea).



<a name="loioc7244c6a7e3b4ffc928a2564c216e7c7__section_ncg_5wm_lgc"/>

## Quotas



### Deployment Quotas

Each tenant is assigned a default quota that limits the number of deployments and replicas per deployment. If you reach this quota, your deployment will not be created and you will be notified accordingly. You can free up your quota by deleting existing deployments.

Alternatively, you can request an increase to your quota by creating a ticket on component `CA-ML-AIC`. Enter the description `Request to Increase Quota` and include details about the size of your increase, whether you want to include deployments, replicas, or both, and your subaccount ID.



### Resource Group Quotas

> ### Restriction:  
> The maximum number of resource groups is limited at tenant level to 50. If you reach this limit, you receive an error message. To free up space, delete some resource groups. Alternatively, raise a ticket to increase your quota.
> 
> For more information, see [Delete a Resource Group](delete-a-resource-group-40d83a2.md).



### Tenant-Wide Generic Secrets Quotas

Each tenant can have a maximum of five tenant-wide secrets. If you reach this limit, you receive an error message. To free up space, delete tenant-wide secrets as described at [Delete a Generic Secret](delete-a-generic-secret-d5d5187.md). Alternatively, submit a ticket to request an increase in your quota.

-   **[Set Up the Free Plan](set-up-the-free-plan-4533adc.md "The Free service plan lets you try out SAP AI Core for testing
		and familiarization purposes at no cost.")**  
The Free service plan lets you try out SAP AI Core for testing and familiarization purposes at no cost.
-   **[Upgrade a Service Plan](upgrade-a-service-plan-924f892.md "Upgrade your SAP AI Core service
		instance from the Free plan to a Standard or Extended plan while keeping your data and
		models.")**  
Upgrade your SAP AI Core service instance from the Free plan to a Standard or Extended plan while keeping your data and models.

**Related Information**  


[Set Up the Free Plan](set-up-the-free-plan-4533adc.md "The Free service plan lets you try out SAP AI Core for testing and familiarization purposes at no cost.")

[SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?service_plan=standard&region=europe(frankfurt)&tab=service_plan)

[SAP BTP Service Description Guide](https://www.sap.com/about/agreements/policies/cloud-platform.html)

[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

