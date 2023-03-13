<!-- loiocc7bacc660a0415a91c372356478298d -->

# Result Sets

A result set is a type of artifact that results from an execution used for batch inferencing.

Result sets are registered as artifacts in the connection where your executions run. Result sets are generated from the workflow executable that is used in your execution process. The execution is not used for a training process, but instead used for batch inferencing and to make predictions on sequential subsets of data.

Result sets are stored as artifacts in your connected hyperscaler object storage. SAP AI Launchpad can be used with multiple hyperscaler object stores, such as Amazon S3, OSS, and WebHDFS.

Result sets are unique to a resource group.

> ### Note:  
> Workflow templates in SAP AI Launchpad are available based on the selected connection to an AI runtime. For more information, see [Workflow Templates](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/83523ab8b49245bcbc9f1bf0969e32d8.html). For information about how to create a workflow executable and include it in your SAP AI Core instance, see [Setting Up Your Git Repository](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/3269092e37d141a293f0dbd7eaafc829.html).

**About Result Set Registration**

-   A result set can be manually registered using SAP AI Launchpad \(see [Register a Result Set](register-a-result-set-0efde3f.md)\). You register a result set using the *ML Operations* app. After you register a result set, you'll see it listed with all other result sets in the app.

-   A result set can be manually registered using SAP AI Core \(see [Create Artifacts](https://help.sap.com/docs/AI_CORE/808d9d442fb0484e9b818924feeb9add/CLOUD/66413f1d9fbf4758a0d739eaf1c95dc7.html)\).


-   **[Register a Result Set](register-a-result-set-0efde3f.md "Use the ML
                                    Operations app to manually register a result set
		that is stored in your object store.")**  
Use the *ML Operations* app to manually register a result set that is stored in your object store.
-   **[Find a Result Set](find-a-result-set-079f5dc.md "Use the ML
                                    Operations app to search for a result
		set.")**  
Use the *ML Operations* app to search for a result set.

**Related Information**  


[Artifact Management](https://help.sap.com/docs/AI_CORE/808d9d442fb0484e9b818924feeb9add/CLOULD/386ba71cbf8c451288b899ec0d8f9fb1.html)

