<!-- loioe6a5a0ea322b4a24abdb73efd7b2fc56 -->

# Batch Consumption

Process large volumes of LLM requests asynchronously in SAP AI Core. Submit a collection of requests as a single input file and the service processes them in the background, then writes the results to your object store.

> ### Note:  
> Batch consumption only supports native LLM calls. Orchestration requests aren't supported.
> 
> Batch consumption is available in EU and US regions, except `prod-euonly` and sovereign cloud deployments.

**For more information about available models, including conversion rates for tokens, rate limits, and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**



## Key Capabilities

-   Process hundreds or thousands of LLM requests in a single submission
-   Reduced cost compared to synchronous inference calls
-   Automatic retry handling for transient provider errors
-   No rate limit management required on the client side



## Prerequisites

-   You have a valid SAP AI Core service instance with access to the generative AI hub. For more information, see [Use a Service Key](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/use-service-key?locale=en-US).
-   You have an object store secret for one of the following supported providers is registered in SAP AI Core. For more information, see [Register Your Object Store Secret](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/register-your-object-store-secret?locale=en-US).
    -   Amazon S3
    -   Azure Blob Storage
    -   Google Cloud Storage
    -   Alibaba Cloud OSS
    -   SAP HANA Cloud, Data Lake




## Workflow

-   Prepare and upload your input file. For more information, see [Prepare and Upload Your Input File](prepare-and-upload-your-input-file-0b9d245.md).
-   Create a batch job that the system processes asynchronously in the background. For more information, see [Create a Batch Job](create-a-batch-job-bb19774.md).
-   Check the status of your batch job. For more information, see [Check Batch Status](check-batch-status-32536ef.md).
-   Retrieve your results from your object store. For more information, see [Retrieve Results](retrieve-results-7d18a48.md).
-   Get the details of your batch. For more information, see [List Batch Jobs](list-batch-jobs-28474fc.md) and [Get Batch Details](get-batch-details-ac0b616.md).
-   Manage the lifecycle of your batch. For more information, see [Cancel a Batch Job](cancel-a-batch-job-17e505c.md) and [Delete a Batch Job](delete-a-batch-job-e3723c2.md).

-   **[Prepare and Upload Your Input File](prepare-and-upload-your-input-file-0b9d245.md "")**  

-   **[Create a Batch Job](create-a-batch-job-bb19774.md "")**  

-   **[Check Batch Status](check-batch-status-32536ef.md "")**  

-   **[Retrieve Results](retrieve-results-7d18a48.md "")**  

-   **[Get Batch Details](get-batch-details-ac0b616.md "")**  

-   **[List Batch Jobs](list-batch-jobs-28474fc.md "")**  

-   **[Cancel a Batch Job](cancel-a-batch-job-17e505c.md "")**  

-   **[Delete a Batch Job](delete-a-batch-job-e3723c2.md "")**  


