<!-- loio08e3d008addb4362986c73ff0151638c -->

# Vector API

Vector API is a set of REST APIs used for document ingestion and retrieval using vector embeddings.

You can use the Vector API to:

-   Create collections.
-   Create documents by directly using chunks of data.
-   Store data in a vector database.
-   Provide repository IDs to access the data.

The vector API incorporates the following units:

**Collections:** A logical container used to store and manage embedded documents.

**Documents:** A unit of text-based content that you upload into a collection, to be used for semantic search and grounding.

**Chunks:** A chunk is a small segment of a document's text, used in the Vector API to improve the accuracy and efficiency of semantic search.

-   **[Preparing Data Using the Vector API](preparing-data-using-the-vector-api-2a9f149.md "Vector API is a microservice provided with a Rest API and endpoints for creating and managing collection and documents.")**  
Vector API is a microservice provided with a Rest API and endpoints for creating and managing collection and documents.
-   **[Vector Search](vector-search-255589a.md "This endpoint allows you to perform a search for relevant chunks within a specific collection or across all collections based on a user
    query. The response includes chunks that match the query, filtered by collection and document metadata. ")**  
This endpoint allows you to perform a search for relevant chunks within a specific collection or across all collections based on a user query. The response includes chunks that match the query, filtered by collection and document metadata.

