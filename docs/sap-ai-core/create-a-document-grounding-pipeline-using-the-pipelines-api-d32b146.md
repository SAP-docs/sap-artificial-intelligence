<!-- loiod32b1465461149749b00129c02e05142 -->

# Create a Document Grounding Pipeline Using the Pipelines API

This API call creates a pipeline for indexing documents for a resource group.



<a name="loiod32b1465461149749b00129c02e05142__section_ljc_ksf_ngc"/>

## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   You have created a generic secret. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).
-   You've added your grounding documents to your document store and you're using a supported data source and document type. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).
-   If you're using metadata, you've configured a metadata server. For more information, see [Prepare your Metadata API Server](prepare-your-metadata-api-server-23a0741.md).



<a name="loiod32b1465461149749b00129c02e05142__section_d3p_kfv_lfc"/>

## Context

You can schedule automatic content updates by using a `cronExpression` when you create your pipeline. For more information, see [Cron Expressions](cron-expressions-6175008.md).

> ### Tip:  
> If you use the pipelines API, you do not need to call the Vector API separately. After the data is embedded, you can directly use the Retrieval API to query the vector store for relevant sections.



<a name="loiod32b1465461149749b00129c02e05142__section_sbw_lw2_pgc"/>

## Procedure

You document grounding pipeline with your chosen repository. For more information, see the following:

-   [Create a Pipeline with Microsoft SharePoint](create-a-pipeline-with-microsoft-sharepoint-80326fe.md)
-   [Create a Pipeline with AWS S3](create-a-pipeline-with-aws-s3-7f97adf.md)
-   [Create a Pipeline with SFTP](create-a-pipeline-with-sftp-3d95d74.md)
-   [Create a Pipeline with SAP Build Work Zone](create-a-pipeline-with-sap-build-work-zone-d499612.md)
-   [Create a Pipeline with SAP Document Management Service](create-a-pipeline-with-sap-document-management-service-5718584.md)



<a name="loiod32b1465461149749b00129c02e05142__section_tgp_1x2_pgc"/>

## Next Steps

You can use API endpoints to view and manage the lifecycle of your data pipelines, executions and documents. For more information, see [Data Pipelines](data-pipelines-9d9eb37.md), [Executions](executions-c70b70d.md) and [Documents](documents-f87ab02.md).

You can manually restart a pipeline. For more information, see [Manually Restart a Document Grounding Pipeline](manually-restart-a-document-grounding-pipeline-932f2b7.md).

-   **[Create a Pipeline with Microsoft SharePoint](create-a-pipeline-with-microsoft-sharepoint-4b8d58c.md "")**  

-   **[Create a Pipeline with AWS S3](create-a-pipeline-with-aws-s3-81634e3.md "")**  

-   **[Create a Pipeline with SFTP](create-a-pipeline-with-sftp-1687f4d.md "")**  

-   **[Create a Pipeline with SAP Build Work Zone](create-a-pipeline-with-sap-build-work-zone-57af498.md "")**  

-   **[Create a Pipeline with SAP Document Management Service](create-a-pipeline-with-sap-document-management-service-306fea4.md "")**  

-   **[Cron Expressions](cron-expressions-6175008.md "")**  


