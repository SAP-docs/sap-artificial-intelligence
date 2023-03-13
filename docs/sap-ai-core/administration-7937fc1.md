<!-- loio7937fc19a06a46db96912017aef4737c -->

# Administration

Creating secrets for your tools, means that you can connect external programs and tools without compromising your account. The tools can be used to incorporate version control, cloud storage and portable containers.

Using SAP AI Core alongside external tools such as GitHub, Docker and Amazon Web Services S3 storage leverages the benefits of version control, containerization and cloud storage. As a result, your content is made available remotely, where you have a stable internet connection.

This section is a one time procedure. It is a dev ops based configuration that connects these tools to your SAP AI Core. You may repeat the steps if necessary, for example to remove or replace access to an external tool.

> ### Note:  
> You must have completed tasks in [Initial Setup](initial-setup-38c4599.md) before configuring your SAP AI Core instance.

-   **[Manage Your Git Repository](manage-your-git-repository-2cd2996.md "You can use your own git repository to version control your SAP AI
									Core templates. The GitOps onboarding to SAP AI
									Core instances involves setting up your git repository and
		synchronizing your content. ")**  
You can use your own git repository to version control your SAP AI Core templates. The GitOps onboarding to SAP AI Core instances involves setting up your git repository and synchronizing your content.
-   **[Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group represents a unique workspace environment, where users can create or add entities such as configurations, executions,
		deployments, and artifacts. ")**  
A resource group represents a unique workspace environment, where users can create or add entities such as configurations, executions, deployments, and artifacts.
-   **[Manage Object Store Secrets](manage-object-store-secrets-f10b532.md "Connect SAP AI
									Core to a cloud object store and manage
		access using an object store secret. The connected storage is used as storage for your dataset, models and other cache files of the Metaflow
		Library for SAP AI
									Core.")**  
Connect SAP AI Core to a cloud object store and manage access using an object store secret. The connected storage is used as storage for your dataset, models and other cache files of the Metaflow Library for SAP AI Core.
-   **[Manage Docker Registry Secrets](manage-docker-registry-secrets-c5445c4.md "Docker facilitates the packaging and running of an application in a remote container. Connect SAP AI
									Core to a Docker repository and manage access using a
		Docker registry secret.")**  
Docker facilitates the packaging and running of an application in a remote container. Connect SAP AI Core to a Docker repository and manage access using a Docker registry secret.

**Parent topic:** [ML Operations](ml-operations-7f5aa9b.md "This section guides you through the end-to-end AI lifecycle of SAP AI Core.")

**Related Information**  


[Connect Your Data](connect-your-data-9508bdb.md "Use cloud storage with SAP AI Core to store AI assets such as datasets and model files. You use Artifacts in SAP AI Core to reference to your AI Assets.")

[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

[Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

[Metrics](metrics-36f8bec.md "The AI API provides the ability to track metrics, and to customize or filter which metrics are reported.")

