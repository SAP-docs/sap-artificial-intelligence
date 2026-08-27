<!-- loio9508bdb9d30c4661b2d4aef7079c20e4 -->

# Connect Your Data

In SAP AI Core, files, which are referred to as artifacts, are the foundation for managing all your AI assets, including datasets, model binaries, and output files. Artifacts are produced or consumed by executions and deployments, and are essential for tracking the lifecycle of your machine learning workflows.

You manage your artifacts by connecting SAP AI Core to your cloud object store \(such as Amazon S3 or Azure Blob Storage\), which lets you store and retrieve artifacts. In this way, you can make sure that your data is secure, scalable, and accessible throughout the ML lifecycle.

To protect your credentials, SAP AI Core uses an object store secret. This secret allows the service to access your cloud storage securely, without exposing sensitive information in code or configuration files.

Every file or data asset is referenced as an artifact within SAP AI Core. This unified approach makes it easy to manage, track, and reuse assets across different projects and workflows.

-   **[Create Files](create-files-66413f1.md "")**  

-   **[List Files](list-files-1d613e0.md "")**  

-   **[Manage Files Using the Dataset API](manage-files-using-the-dataset-api-ba8ac5c.md "Where direct access to files in the object store is not possible or desirable (for example, in Content as a Service Scenarios, where the
		Service Consumers might not be the owners of the object store) you can upload, download, and delete files from the pre-registered object store
		using the SAP AI Core Dataset API. ")**  
Where direct access to files in the object store is not possible or desirable \(for example, in Content as a Service Scenarios, where the Service Consumers might not be the owners of the object store\) you can upload, download, and delete files from the pre-registered object store using the SAP AI Core Dataset API.

