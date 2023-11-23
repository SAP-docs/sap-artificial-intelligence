<!-- loioac3d92b6fe604ede99a382be5b1008e5 -->

# Custom Runtime Capabilities Using the Meta API

The AI API `Meta API` is used to identify what capabilities are applicable for a given AI service or runtime. The SAP AI Launchpad then shows the capabilities in the user interface.

The AI API offers rich capabilities for AI use cases on your workload engine. However, not all services require all capabilities. Capabilities are enabled or disabled for your service based on the specific requirements of your AI use case, and the needs of users of your service. The `Meta API` is used to hide unnecessary capabilities in the underlying service and consequently, only those that are applicable are present in the user interface.

The `Meta API` reduces the impact of API changes, ensuring that users are not confronted with capabilities they do not use, resulting in a streamlined and robust launchpad experience.

The SAP Runtime team disables or enables capabilities in the `Meta API`.

To learn more about the capabilities provided by `Meta API`, see [AI API Runtime Impementations](https://help.sap.com/docs/AI_CORE/52b4adb30e6744709d6226d2b0659dea/dbacc5fee07c4e43a656f5d1203654c7.html).

> ### Example:  
> You have service `A`. This service has the capability to let users create their own deployments but there is no capability to run executions. The capability required to support service `A` is `userDeployments`, and not `userExecutions`. SAP AI Launchpad uses the metadata associated with the capability settings to hide the corresponding user interface for executions.

Metadata for capabilities can be refreshed on-demand by users. Capability metadata is also refreshed periodically according to a predefined schedule.

