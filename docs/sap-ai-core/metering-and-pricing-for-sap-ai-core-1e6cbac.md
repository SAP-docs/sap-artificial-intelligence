<!-- loio1e6cbac9c2cb4dcba7929035982a7e7b -->

# Metering and Pricing for SAP AI Core

SAP AI Core provides a scalable infrastructure for AI model management, with usage-based pricing that lets you pay only for the resources you use.

The service offers various plans, including a free, standard, and extended plan. If you want to access all capabilities, we recommend the extended plan.

We offer the following model options:

-   Generative AI with SAP-hosted, SAP-managed, and remote foundation models, and pipelines such as grounding
-   Predictive AI with your custom AI models

You have the flexibility to select the model options that best suit your needs.

Custom AI models incur compute, storage, and baseline costs. The system automatically applies baseline charges every hour, up to a maximum of 730 hours.

If you use foundation models and grounding, the platform waives compute, storage, and baseline costs. Instead, charges accrue based on the number of tokens used by the foundation models.



<a name="loio1e6cbac9c2cb4dcba7929035982a7e7b__section_lgg_glj_kfc"/>

## More Information

For more information about the potential costs associated with using foundation models and grounding in SAP AI Core, including metering information, example pricing calculations, and typical consumption patterns, see [Metering and Pricing for Generative AI](metering-and-pricing-for-generative-ai-41e8d85.md).

For more information about the potential costs associated with using custom AI models in SAP AI Core, including metering information, example pricing calculations, and typical consumption patterns, see [Metering and Pricing for Predictive AI](metering-and-pricing-for-predictive-ai-32f8775.md).



<a name="loio1e6cbac9c2cb4dcba7929035982a7e7b__section_jyq_v21_1fc"/>

## Consumption Information

To see detailed consumption information in SAP BTP cockpit, open your global account and click *Usage* from the navigation panel. Filter by AI Core and click Export. The report contains generative AI hub model consumption under *Applications* and resource group level consumption under *instance*.

For more information, see [Monitoring Usage and Consumption Costs in Your Global Account in SAP BTP.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/de6f0db8919f4e6f97e54bc4ddaf2ab8.html)

-   **[Metering and Pricing for Generative AI](metering-and-pricing-for-generative-ai-41e8d85.md "The use of generative AI in SAP AI Core is measured
		using tokens, which are converted into capacity units based on input and output volume.
		Billing is calculated according to these capacity units and varies by model type and usage
		pattern.")**  
The use of generative AI in SAP AI Core is measured using tokens, which are converted into capacity units based on input and output volume. Billing is calculated according to these capacity units and varies by model type and usage pattern.
-   **[Metering and Pricing for Predictive AI](metering-and-pricing-for-predictive-ai-32f8775.md "")**  


