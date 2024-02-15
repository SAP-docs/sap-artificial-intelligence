<!-- loio44d7acf7ebe3406cbe457388cca97e86 -->

# Deletion

SAP AI Core supports **Bring your object store**, whereby customers register the object store secret where artifact relevant files \(such as training data or machine learning models or other types\) are stored. Such data is used by the ML workloads during processing, such as ML Training or ML Serving.

The notion of artifacts is limited to capture the metadata of the data. Data is physically stored in the object store and SAP AI Core is not responsible for deletion of files. When artifacts are deleted using AI API, corresponding metadata are deleted from SAP AI Core service and the actual files are not deleted from the object store. For more information about the AI API, see [AI API Overview](ai-api-overview-716d4c3.md).

Upon offboarding, SAP AI Core will clean up the cached data within AI Core used for processing purposes.

SAP AI Core customers, as Data Controllers, are responsible for deletion of data from the registered object store.

