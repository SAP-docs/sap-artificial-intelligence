<!-- loioe299ed5d24224dde80bacb52c2a057de -->

# Datasets

A dataset is a type of artifact which is registered in your AI runtime. A registered dataset references files that are stored in your connected hyperscaler object store.

Data is uploaded to your hyperscaler object store as a single file \(such as a `CSV` file\) or as multiple files \(such as images\). The data is then registered as a dataset with a unique ID. You can use the dataset ID in a configuration as an input artifact value in a workflow executable.

SAP AI Launchpad can be used with multiple hyperscaler object stores, such as Amazon S3, OSS, and WebHDFS.

Datasets are unique to a resource group.

**About Dataset Registration**

-   A dataset can be manually registered using SAP AI Launchpad \(see [Register a Dataset](register-a-dataset-a63c2f5.md)\). You register a dataset using the *ML Operations* app. After you register a dataset, you'll see it listed with all other datasets in the app.

-   A dataset can be manually registered using SAP AI Core \(see [Create Artifacts](https://help.sap.com/docs/AI_CORE/808d9d442fb0484e9b818924feeb9add/CLOUD/66413f1d9fbf4758a0d739eaf1c95dc7.html)\).


-   **[Register a Dataset](register-a-dataset-a63c2f5.md "Use the ML
                                    Operations app to manually register a dataset that
		is stored in your object store.")**  
Use the *ML Operations* app to manually register a dataset that is stored in your object store.
-   **[Find a Dataset](find-a-dataset-de82ced.md "Use the ML
                                    Operations app to search for a
		dataset.")**  
Use the *ML Operations* app to search for a dataset.

**Related Information**  


[Artifact Management](https://help.sap.com/docs/AI_CORE/808d9d442fb0484e9b818924feeb9add/CLOULD/386ba71cbf8c451288b899ec0d8f9fb1.html)

