<!-- loioff2bf23727194e8e81d1a2f3c92b05aa -->

# Metadata Management API



## Overview

The Metadata Management API provides endpoints for managing metadata configurations and document metadata within the document grounding pipelines. You can create and manage metadata configurations for various data repositories, enumerate documents, and update document metadata in batch operations.



## Key Capabilities

The Metadata Management API enables you to:

-   Create and manage metadata configurations for different repository types.
-   Retrieve metadata configurations with pagination support and detailed status information.
-   Enumerate documents automatically from configured repositories.
-   List and filter documents within metadata configurations using path-based queries.
-   Update document metadata in batch for up to 1,000 documents per request.
-   Manage the lifecycle of your metadata configurations.



<a name="loioff2bf23727194e8e81d1a2f3c92b05aa__section_dxk_glv_vfc"/>

## API Request Format

When you build your API requests, follow the format outlined in the *Pipelines* section of the Grounding API. For more information, see [Grounding API](https://api.sap.com/api/DOCUMENT_GROUNDING_API/resource/Retrieval).

The endpoint for the pipelines API is `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations`.

-   **[Create a Metadata Configuration](create-a-metadata-configuration-51a3fe1.md "Creates a new metadata configuration and triggers document enumeration for the configured repository. ")**  
Creates a new metadata configuration and triggers document enumeration for the configured repository.
-   **[List Metadata Configurations](list-metadata-configurations-c9f00ae.md "Retrieves a paginated list of all available metadata configurations. ")**  
Retrieves a paginated list of all available metadata configurations.
-   **[Get a Metadata Configuration by ID](get-a-metadata-configuration-by-id-674efc3.md "Retrieves the details of a specific metadata configuration by its ID.")**  
Retrieves the details of a specific metadata configuration by its ID.
-   **[Delete a Metadata Configuration](delete-a-metadata-configuration-13cc4da.md "Delete a specific metadata configuration by its ID.")**  
Delete a specific metadata configuration by its ID.
-   **[List the Documents of a Metadata Configuration](list-the-documents-of-a-metadata-configuration-3cc2e3a.md "Retrieves a paginated list of documents associated with a metadata configuration. ")**  
Retrieves a paginated list of documents associated with a metadata configuration.
-   **[Get Details of a Document](get-details-of-a-document-37b6c1f.md "Retrieves details of a document associated with a metadata configuration by document ID. ")**  
Retrieves details of a document associated with a metadata configuration by document ID.
-   **[Batch Update Document Metadata](batch-update-document-metadata-4fad8fc.md "Updates the metadata for multiple documents within a specific metadata configuration in a single request.")**  
Updates the metadata for multiple documents within a specific metadata configuration in a single request.

