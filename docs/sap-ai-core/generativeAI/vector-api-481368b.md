<!-- copy481368b37ac34ba29255e953fe753b62 -->

# Vector API

Vector API is a set of REST APIs used for document ingestion and retrieval using vector embeddings.

You can use the Vector API to:

-   Create collections.
-   Create documents by directly using chunks of data.
-   Store data in a vector database.
-   Provide repository IDs to access the data.

The Vector API incorporates the following units:

**Collections:** A logical container used to store and manage embedded documents.

**Documents:** A unit of text-based content that you upload into a collection, to be used for semantic search and grounding.

**Chunks:** A small segment of a document's text, used in the Vector API to improve the accuracy and efficiency of semantic search.



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

-   **[Preparing Data Using the Vector API](preparing-data-using-the-vector-api-fa7964a.md "Vector API is a microservice provided with a Rest API and endpoints for creating and managing collection and documents.")**  
Vector API is a microservice provided with a Rest API and endpoints for creating and managing collection and documents.
-   **[Metadata](metadata-dd57ee7.md "")**  

-   **[Vector Search](vector-search-68096f8.md "This endpoint allows you to perform a search for relevant chunks within a specific
    collection or across all collections based on a user query. The response includes chunks that
    match the query, filtered by collection and document metadata.")**  
This endpoint allows you to perform a search for relevant chunks within a specific collection or across all collections based on a user query. The response includes chunks that match the query, filtered by collection and document metadata.

