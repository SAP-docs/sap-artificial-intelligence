<!-- loio6348a01a930d414ab7ac7ab522d81eb5 -->

# Data Management APIs

Using the Document Grounding APIs, you can automate the process of retrieving, preprocessing, and embedding documents from supported data sources into the SAP HANA Vector Store. These APIs handle the end-to-end flow of documents, including document fetching, text chunking, and embedding via the Vector API, without requiring you to manage each step manually.

For document processing and vector generation, the following options are available:

-   For use cases where documents are stored in a repository, the **Pipelines API** is recommended.

    The **Pipelines API** creates data management pipelines that fetch documents from a supported data source, preprocess and chunk those documents, and store their semantic embeddings in the HANA Vector Store. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).

-   For use cases where documents are uploaded and managed directly, the **Vector API** is recommended.

    The **Vector API** preprocesses documents into chunks and stores their semantic embeddings in collections. For more information, see [Vector API](vector-api-08e3d00.md).


The **Retrieval API** performs similarity searches on the vector database for information retrieval. It can be used for repositories of documents that have been processed using the Pipelines API, or for collections that have been processed using the Vector API. For more information, see [Preparing Data Using the Vector API](preparing-data-using-the-vector-api-2a9f149.md).

> ### Tip:  
> If you use the Pipelines API, you don't also need to call the Vector API. After the data is embedded, you can directly use the Retrieval API to query the vector store for relevant results.

For more information about the API, such as request formats, response schemas, authentication headers, and supported operations, see [Grounding APIs in the Business Accelerator Hub](https://api.sap.com/api/DOCUMENT_GROUNDING_API/resource/Pipelines).



## Rate Limits

The following rate limits apply:


<table>
<tr>
<th valign="top">

Operation Type

</th>
<th valign="top">

Call Type

</th>
<th valign="top">

Rate Limit

</th>
</tr>
<tr>
<td valign="top">

write\_pipeline

</td>
<td valign="top">

POST – Create pipeline

</td>
<td valign="top">

5 requests per minute

</td>
</tr>
<tr>
<td valign="top">

write

</td>
<td valign="top">

PUT, POST, DELETE, PATCH

</td>
<td valign="top">

6 requests per second

</td>
</tr>
<tr>
<td valign="top">

read

</td>
<td valign="top">

GET

</td>
<td valign="top">

1200 requests per minute

</td>
</tr>
</table>



## Capacity Quotas and Input Limits



### Vector Ingestion – Capacity Limits

The following capacity limits apply:


<table>
<tr>
<th valign="top">

Category

</th>
<th valign="top">

Description

</th>
<th valign="top">

Limit Type

</th>
<th valign="top">

Limit

</th>
</tr>
<tr>
<td valign="top">

Collections

</td>
<td valign="top">

Max collections

</td>
<td valign="top">

Quota

</td>
<td valign="top">

55,000

</td>
</tr>
<tr>
<td valign="top">

Documents

</td>
<td valign="top">

Max documents per collection

</td>
<td valign="top">

Quota

</td>
<td valign="top">

100,000

</td>
</tr>
<tr>
<td valign="top">

Documents

</td>
<td valign="top">

Max documents per ingestion request

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

100

</td>
</tr>
<tr>
<td valign="top">

Chunks

</td>
<td valign="top">

Max chunks per document

</td>
<td valign="top">

Quota

</td>
<td valign="top">

200,000

</td>
</tr>
</table>



### Metadata Limits \(Ingestion and Query Time\)

The following metadata limits apply:


<table>
<tr>
<th valign="top">

Metadata Type

</th>
<th valign="top">

Limit Type

</th>
<th valign="top">

Limit

</th>
</tr>
<tr>
<td valign="top">

Collection Metadata

</td>
<td valign="top">

Quota / Input Limit

</td>
<td valign="top">

500 / 5,000

</td>
</tr>
<tr>
<td valign="top">

Document Metadata

</td>
<td valign="top">

Quota / Input Limit

</td>
<td valign="top">

500 / 5,000

</td>
</tr>
<tr>
<td valign="top">

Chunk Metadata

</td>
<td valign="top">

Quota / Input Limit

</td>
<td valign="top">

500 / 5,000

</td>
</tr>
</table>



### Vector Search – Query Limits

The following query limits apply:


<table>
<tr>
<th valign="top">

Category

</th>
<th valign="top">

Description

</th>
<th valign="top">

Limit Type

</th>
<th valign="top">

Limit

</th>
</tr>
<tr>
<td valign="top">

Filters

</td>
<td valign="top">

Max filters per query

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

15

</td>
</tr>
<tr>
<td valign="top">

Collections

</td>
<td valign="top">

Max collection IDs per query

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

5,000

</td>
</tr>
<tr>
<td valign="top">

Results

</td>
<td valign="top">

Max chunk results per query

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

100

</td>
</tr>
<tr>
<td valign="top">

Results

</td>
<td valign="top">

Max document results per query

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

10

</td>
</tr>
</table>



### Retrieval Search – Query Limits

The following query limits apply:


<table>
<tr>
<th valign="top">

Category

</th>
<th valign="top">

Description

</th>
<th valign="top">

Limit Type

</th>
<th valign="top">

Limit

</th>
</tr>
<tr>
<td valign="top">

Filters

</td>
<td valign="top">

Max filters per query

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

15

</td>
</tr>
<tr>
<td valign="top">

Collections

</td>
<td valign="top">

Max collection IDs per query

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

5,000

</td>
</tr>
<tr>
<td valign="top">

Results

</td>
<td valign="top">

Max chunk results per query

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

100

</td>
</tr>
<tr>
<td valign="top">

Results

</td>
<td valign="top">

Max document results per query

</td>
<td valign="top">

Input Limit

</td>
<td valign="top">

10

</td>
</tr>
</table>

-   **[Metadata Management API](metadata-management-api-ff2bf23.md "")**  

-   **[Pipelines API](pipelines-api-d8cc0e3.md "The Pipelines API allows you to provide unstructured documents from your data repositories, and create a document grounding pipeline for
		your resource group.")**  
The Pipelines API allows you to provide unstructured documents from your data repositories, and create a document grounding pipeline for your resource group.
-   **[Vector API](vector-api-08e3d00.md "Vector API is a set of REST APIs used for document ingestion and retrieval using vector embeddings.")**  
Vector API is a set of REST APIs used for document ingestion and retrieval using vector embeddings.
-   **[Retrieval API](retrieval-api-281e8cf.md "The Retrieval API lets you retrieve repositories or collections created through the Vector API. It also lets you perform similarity
		searches on the vector database to obtain relevant chunks and documents.")**  
The Retrieval API lets you retrieve repositories or collections created through the Vector API. It also lets you perform similarity searches on the vector database to obtain relevant chunks and documents.

