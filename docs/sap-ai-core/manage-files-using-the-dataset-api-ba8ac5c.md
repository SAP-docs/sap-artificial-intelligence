<!-- loioba8ac5c1b8644a9a978bd1a3cf870660 -->

# Manage Files Using the Dataset API

Where direct access to files in the object store is not possible or desirable \(for example, in Content as a Service Scenarios, where the Service Consumers might not be the owners of the object store\) you can upload, download, and delete files from the pre-registered object store using the SAP AI Core Dataset API.

For full details on the Dataset API specification, see [SAP AI Core API documentation](https://api.sap.com/api/AI_CORE_API/overview).



<a name="loioba8ac5c1b8644a9a978bd1a3cf870660__section_yzv_d5s_2xb"/>

## Prerequisites

-   You must have an object store secret defined in the target resource group.

> ### Restriction:  
> Only S3 object stores can be used with the Dataset API.

> ### Restriction:  
> Only `csv` type files can be uploaded with the Dataset API.

-   **[Create Files](create-files-0466459.md "")**  

-   **[Download Files](download-files-0a641f3.md "")**  

-   **[Delete Files](delete-files-edf9b1b.md "")**  


**Parent topic:**[Connect Your Data](connect-your-data-9508bdb.md "Use cloud storage with SAP AI Core to store AI assets such as datasets and model files. You use Artifacts in SAP AI Core to reference to your AI Assets.")

**Related Information**  


[Manage Files](manage-files-386ba71.md "An artifact refers to data or a file that is produced or consumed by executions or deployments. They are managed through SAP AI Core and your connected object store.")

