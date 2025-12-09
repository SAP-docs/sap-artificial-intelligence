<!-- copy07adea99628146a68867a9d2fad5305d -->

# Pipelines API

The Pipelines API allows you to provide unstructured documents from your data repositories, and create a document grounding pipeline for your resource group.

The API is proxied through the generative AI hub and incorporates vector stores, such as the managed HANA database.

Each pipeline represents a configured end-to-end process including the following steps:

1.  Fetches documents from a supported data source

2.  Preprocesses and chunks the document content, and generates semantic embeddings. Semantic embeddings are multidimensional representations of textual information.

3.  Stores semantic embeddings into the HANA Vector Store




<a name="copy07adea99628146a68867a9d2fad5305d__section_efy_n2s_dgc"/>

## Data Repositories

The following repositories and document types are supported:

-   Microsoft SharePoint

-   AWS S3

-   SFTP

-   SAP Build Work Zone

-   SAP Document Management service



<table>
<tr>
<th valign="top">

Document Repository

</th>
<th valign="top">

Document \(File\) Format

</th>
<th valign="top">

Content Refresh

</th>
<th valign="top">

Document Content

</th>
<th valign="top">

Maximum Number of Documents

</th>
</tr>
<tr>
<td valign="top">

Microsoft SharePoint

</td>
<td valign="top">

PDF, HTML, TXT, JPEG, JPG, DOCX, PNG, TIFF, PPT

</td>
<td valign="top">

Daily

</td>
<td valign="top">

Plain Text

PPT only: Images, Plain Text, Table

</td>
<td valign="top">

Maximum of 2000 Documents per Pipeline

</td>
</tr>
<tr>
<td valign="top">

AWS S3

</td>
<td valign="top">

PDF, HTML, TXT, JPEG, JPG, DOCX, PNG, TIFF, PPT

</td>
<td valign="top">

Daily

</td>
<td valign="top">

Plain Text

PPT only: Images, Plain Text, Table

</td>
<td valign="top">

Maximum of 2000 Documents per Pipeline

</td>
</tr>
<tr>
<td valign="top">

SFTP

</td>
<td valign="top">

PDF, HTML, TXT, JPEG, JPG, DOCX, PNG, TIFF, PPT

</td>
<td valign="top">

Daily

</td>
<td valign="top">

Plain Text

PPT only: Images, Plain Text, Table

</td>
<td valign="top">

Maximum of 2000 Documents per Pipeline

</td>
</tr>
<tr>
<td valign="top">

SAP Document Management service

</td>
<td valign="top">

PDF, HTML, TXT, JPEG, JPG, DOCX, PNG, TIFF, PPT

</td>
<td valign="top">

Daily

</td>
<td valign="top">

Plain Text

PPT only: Images, Plain Text, Table

</td>
<td valign="top">

Maximum of 2000 Documents per Pipeline

</td>
</tr>
</table>



<a name="copy07adea99628146a68867a9d2fad5305d__section_dxk_glv_vfc"/>

## API Request Format

When you build your API requests, follow the format outlined in the *Pipelines* section of the Grounding API. For more information, see [Grounding API](https://api.sap.com/api/DOCUMENT_GROUNDING_API/resource/Retrieval).

The endpoint for the pipelines API is `$AI_API_URL/v2/lm/document-grounding/pipelines`.

For region and pricing information, see SAP Note [3437766](https://me.sap.com/notes/3437766).

> ### Caution:  
> Do not expose personally identifiable or privileged information in the documents exposed to your pipeline when using generative AI hub. Personally identifiable information is any data that can be used alone, or in combination, to identify the person that the data refers to. The document grounding capability has no mechanism for determining the type of data that it processes, and does not filter confidential or other privileged information.

-   **[Create a Document Grounding Pipeline Using the Pipelines API](create-a-document-grounding-pipeline-using-the-pipelines-api-0a13e1c.md "This API call creates a pipeline for indexing documents for a resource group.")**  
This API call creates a pipeline for indexing documents for a resource group.
-   **[Data Pipelines](data-pipelines-4af7e1f.md "")**  

-   **[Executions](executions-60d428a.md "")**  

-   **[Documents](documents-1741023.md "")**  

-   **[Manually Restart a Document Grounding Pipeline](manually-restart-a-document-grounding-pipeline-b8e880a.md "This endpoint allows you to retrain an existing pipeline manually. ")**  
This endpoint allows you to retrain an existing pipeline manually.
-   **[Search a Pipeline](search-a-pipeline-5e2f4aa.md "")**  


**Related Information**  


[SAP Document Management Service](https://help.sap.com/docs/DOCUMENT_MANAGEMENT/f6e70dd4bffa4b65965b43feed4c9429/72f18b043abd463aba2a680edc897439.html)

