<!-- loioa9badce6a4da4df68e98549d64aa2217 -->

# Pipeline API

The Pipeline API allows you to provide unstructured documents from your data repositories.

The API is proxied through the generative AI hub and incorporates vector stores, such as the managed HANA database. This pipeline segments data into chunks and generates embeddings, which are multidimensional representations of textual information. These embeddings are stored in a vector database.

The Pipeline API is compatible with the following data repositories:


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

PDF, DOCX

</td>
<td valign="top">

Daily

</td>
<td valign="top">

Plain Text

</td>
<td valign="top">

Maximum of 2000 Documents

</td>
</tr>
<tr>
<td valign="top">

AWS S3

</td>
<td valign="top">

PDF, DOCX

</td>
<td valign="top">

Daily

</td>
<td valign="top">

Plain Text

</td>
<td valign="top">

Maximum of 2000 Documents

</td>
</tr>
<tr>
<td valign="top">

SFTP

</td>
<td valign="top">

PDF, DOCX

</td>
<td valign="top">

Daily

</td>
<td valign="top">

Plain Text

</td>
<td valign="top">

Maximum of 2000 Documents

</td>
</tr>
</table>

For region and pricing information, see SAP Note [3437766](https://me.sap.com/notes/3437766).

> ### Caution:  
> Do not expose personally identifiable or privileged information in the documents exposed to your pipeline when using generative AI hub. Personally identifiable information is any data that can be used alone, or in combination, to identify the person that the data refers to. The document grounding capability has no mechanism for determining the type of data that it processes, and does not filter confidential or other privileged information.

-   **[Preparing Data Using the Pipeline API](preparing-data-using-the-pipeline-api-9c972e2.md "This API call creates a pipeline for indexing documents.")**  
This API call creates a pipeline for indexing documents.
-   **[Manage Data Pipelines](manage-data-pipelines-2f94a67.md "")**  


