<!-- loioa9badce6a4da4df68e98549d64aa2217 -->

# Pipeline API

The Pipeline API allows you to provide unstructured documents from your data repositories.

The API is proxied through the generative AI hub and incorporates vector stores, such as the managed HANA database. This pipeline segments data into chunks and generates embeddings, which are multidimensional representations of textual information. These embeddings are stored in a vector database.

The Pipeline API is compatible with the following data repositories:

-   **Microsoft SharePoint:**

    -   Maximum of 2000 documents

    -   `PDF`, `DOCX` file types

    -   Plain text format

    -   Content is updated once each day


-   **SAP Help Portal:** Content available at [http://help.sap.com](http://help.sap.com) is supported.

For region and pricing information, see SAP Note [350347](https://me.sap.com/notes/350347).

-   **[Preparing Data Using the Pipeline API](preparing-data-using-the-pipeline-api-9c972e2.md "This API call creates a pipeline for indexing documents.")**  
This API call creates a pipeline for indexing documents.

