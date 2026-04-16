<!-- copy68096f88b52f4beebe56d0c7e59150f5 -->

# Vector Search

This endpoint allows you to perform a search for relevant chunks within a specific collection or across all collections based on a user query. The response includes chunks that match the query, filtered by collection and document metadata.



<a name="copy68096f88b52f4beebe56d0c7e59150f5__future"/>

## Metadata Filtering Overview

Metadata Filtering lets you retrieve and filter documents, collections, and chunks with advanced metadata queries. It supports flexible, multi-level filtering to give you control over search results.

> ### Note:  
> Filtering is available at the collection, document, and chunk levels.

The following are the match modes supports :



### Key Match Modes

**Simple Matching**

-   Provide `key-value` pairs in the `"chunkMetadata"`, `"documentMetadata"`, or `"collectionMetadata"` fields.
-   Each entry defines a metadata key and a list of valid values.
-   All specified `key-value` pairs must match for an item to be returned \(logical **AND** across keys\).
-   Items containing all the given metadata values are included in the results.

**Complex Matching**

-   Define `key-value` pairs using nested logical expressions in the filter field.
-   Use logical operators \(**AND**, **OR**\) to combine multiple conditions.
-   Each condition can define the metadata key, values, and the scope \(collection, document, or chunk\).
-   Filters can be nested to create more advanced queries.

> ### Tip:  
> Complex filtering is recommended because it offers greater flexibility and is the recommended approach.



### Values Match Modes

**Match Modes**

-   **ANY** 
    -   At least one metadata value matches.
    -   This is the default match mode.
    -   Defined only at injection time.

-   **ALL**
    -   All document metadata values must match exactly, or be a subset of the search metadata.
    -   Supported only at the document level.
    -   Defined only at injection time.


**Select Modes**

-   Supports `ignoreIfKeyAbsent` to control how missing keys are handled. This option can be set at query time and is supported only at the document level.
-   The default is `False`.
-   When set to `True`, documents that do not contain the specified key are also included in the results.



## Procedure

Send a POST request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/search`

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

\{\{resource\_group\}\}

</td>
<td valign="top">

The AI resource group assigned to your account

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
<tr>
<td valign="top">

\{\{access\_token\}\}

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

query

</td>
<td valign="top">

Your user query

</td>
</tr>
<tr>
<td valign="top">

collectionIds

</td>
<td valign="top">

Enter <code>“*”</code> to search all collections or add a collectionId to search a specific collection. To search more than one specific collection, add `collectionIds` in a comma separated list.

</td>
</tr>
<tr>
<td valign="top">

documentMetadata

</td>
<td valign="top">

Filters based on metadata previously assigned

</td>
</tr>
</table>



## Example with Simple Matching

> ### Sample Code:  
> ```
> curl --request POST \   
>   --url $AI_API_URL/v2/lm/document-grounding/vector/search \
>   --header 'AI-Resource-Group: {{resource_group}}' \  
>   --header 'Content-Type: application/json' \  
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{ 
>   "query": "is Joule an AI Copilot?",  
>   "filters": [ 
>     { 
>       "id": "String", 
>       "collectionIds": ["*"], 
>       "configuration": {}, 
>       "collectionMetadata": [], 
>       "documentMetadata": [
>         { 
>           "key": "url", 
>           "value": [ 
>             "http://hello.com", 
>             "1234" 
>           ] 
>         } 
>       ], 
>       "chunkMetadata": [] 
>     } 
>   ] 
> }'
> ```



## Example with Complex Matching

Use the following examples to define grounding metadata filters. The example below shows a filter that retrieves content matching the following metadata specification:

-   `key1=["value1"]`OR `key2=["value2"]`

-   `(key1=["value1"]`AND `key2=["value2"])` OR `key3=["value3"]`

-   `(key1=["value1"]` AND `key2=["value2"])` OR `key3=["value3"]`

-   `key1=["value1"]` AND `key2=["value2"]`


> ### Sample Code:  
> ```
> curl --request POST \   
>   --url $AI_API_URL/v2/lm/document-grounding/vector/search \
>   --header 'AI-Resource-Group: {{resource_group}}' \  
>   --header 'Content-Type: application/json' \  
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{ 
>   "query": "is Joule an AI Copilot?",  
>   "filters": [ 
>     { 
>       "id": "String", 
>       "collectionIds": ["*"], 
>       "configuration": {}, 
>       "collectionMetadata": [], 
>       "documentMetadata": [],
>       "chunkMetadata": [],
>       "filter": {
>         "operator": "and",
>         "left": {
>           "key": "key1",
>           "value": [
>           "value1"
>           ],
>           "scope": "document"
>         },
>         "right": {
>           "key": "key2",
>           "value": [
>           "value2"
>           ],
>           "scope": "document"
>         }
>       }
>     } 
>   ] 
> }'
> ```



## Nested Complex Matching

The following example shows a complex filter with nested conditions. It retrieves all content where the chunk has `key1=value1`, and either the document has `key2=value2` or the collection has `key3=value3`.

> ### Sample Code:  
> ```
> curl --request POST \   
>   --url $AI_API_URL/v2/lm/document-grounding/vector/search \
>   --header 'AI-Resource-Group: {{resource_group}}' \  
>   --header 'Content-Type: application/json' \  
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{ 
>   "query": "is Joule an AI Copilot?",  
>   "filters": [ 
>     { 
>       "id": "String", 
>       "collectionIds": ["*"], 
>       "configuration": {}, 
>       "collectionMetadata": [], 
>       "documentMetadata": [], 
>       "chunkMetadata": [],
>       "filter": {
>         "operator": "and",
>         "left": {
>           "key": "key1",
>           "value": [
>             "value1"
>           ],
>           "scope": "chunk"
>         },
>         "right": {
>           "operator": "or",
>           "left": {
>             "key": "key2",
>             "value": [
>               "value2"
>             ],
>             "scope": "document"
>           },
>           "right": {
>             "key": "key3",
>             "value": [
>               "value3"
>             ],
>             "scope": "collection"
>           }
>         }
>       }
>     } 
>   ] 
> }'
> ```



## Nested Complex Filter with Match Mode ALL

The document is created with metadata where `key1=["value11"]` uses the default match mode **ANY**, and `key2=["value21","value22"]` uses match mode **ALL**. The search request contains both keys at the document level.

Because the document's`key2` contains the full set of requested values, the document matches the filter and is returned.

> ### Sample Code:  
> ```
> curl --request POST \   
>   --url $AI_API_URL/v2/lm/document-grounding/vector/search \
>   --header 'AI-Resource-Group: {{resource_group}}' \  
>   --header 'Content-Type: application/json' \  
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{ 
>   "query": "is Joule an AI Copilot?",  
>   "filters": [ 
>     { 
>       "id": "String", 
>       "collectionIds": ["*"], 
>       "configuration": {}, 
>       "collectionMetadata": [], 
>       "documentMetadata": [],
>       "chunkMetadata": [],
>       "filter": {
>         "operator": "and",
>         "left": {
>           "key": "key1",
>           "value": [
>           "value11"
>           ],
>           "scope": "document"
>         },
>         "right": {
>           "key": "key2",
>           "value": [
>           “value21”, "value22", “value23”
>           ],
>           "scope": "document"
>         }
>       }
>     } 
>   ] 
> ```



The response is returned in JSON format, and includes relevant chunks based on similarity search. Each chunk object has a `searchScores` object, describing how relevant the chunk is to the search query.

The results also contain a `denseRetrievalScore` containing the cosine similarity score of the text embeddings.

<a name="reference_z45_t22_wfc"/>

<!-- reference\_z45\_t22\_wfc -->

## Payload Attributes


<table>
<tr>
<th valign="top">

Attribute

</th>
<th valign="top">

Type

</th>
<th valign="top">

Required

</th>
<th valign="top">

Description

</th>
<th valign="top">

Constraints

</th>
</tr>
<tr>
<td valign="top">

query

</td>
<td valign="top">

string

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The search query text

</td>
<td valign="top">

maxLength: 2000, minLength: 1

</td>
</tr>
<tr>
<td valign="top">

filters

</td>
<td valign="top">

array

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Array of search filters

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

filters\[\].id

</td>
<td valign="top">

string

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Unique identifier for this search filter

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

filters\[\].collectionIds

</td>
<td valign="top">

array of strings

</td>
<td valign="top">

Yes

</td>
<td valign="top">

List of collection IDs to search in. Use \["\*"\] to search all collections

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

filters\[\].configuration

</td>
<td valign="top">

object

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Search configuration options

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

filters\[\].configuration.maxChunkCount

</td>
<td valign="top">

integer

</td>
<td valign="top">

No

</td>
<td valign="top">

Maximum number of chunks to return

</td>
<td valign="top">

\> 0, cannot be used with maxDocumentCount

</td>
</tr>
<tr>
<td valign="top">

filters\[\].configuration.maxDocumentCount

</td>
<td valign="top">

integer

</td>
<td valign="top">

No

</td>
<td valign="top">

Maximum number of documents to return

</td>
<td valign="top">

\> 0, cannot be used with maxChunkCount

</td>
</tr>
<tr>
<td valign="top">

filters\[\].collectionMetadata

</td>
<td valign="top">

array

</td>
<td valign="top">

No

</td>
<td valign="top">

Metadata filters for collections

</td>
<td valign="top">

maxItems: 2000

</td>
</tr>
<tr>
<td valign="top">

filters\[\].collectionMetadata\[\].key

</td>
<td valign="top">

string

</td>
<td valign="top">

Yes \(if parent used\)

</td>
<td valign="top">

Metadata key to filter on

</td>
<td valign="top">

maxLength: 1024

</td>
</tr>
<tr>
<td valign="top">

filters\[\].collectionMetadata\[\].value

</td>
<td valign="top">

array of strings

</td>
<td valign="top">

Yes \(if parent used\)

</td>
<td valign="top">

Acceptable values for the key

</td>
<td valign="top">

maxLength per item: 1024

</td>
</tr>
<tr>
<td valign="top">

filters\[\].documentMetadata

</td>
<td valign="top">

array

</td>
<td valign="top">

No

</td>
<td valign="top">

Metadata filters for documents

</td>
<td valign="top">

maxItems: 2000

</td>
</tr>
<tr>
<td valign="top">

filters\[\].documentMetadata\[\].key

</td>
<td valign="top">

string

</td>
<td valign="top">

Yes \(if parent used\)

</td>
<td valign="top">

Document metadata key to filter on

</td>
<td valign="top">

maxLength: 1024

</td>
</tr>
<tr>
<td valign="top">

filters\[\].documentMetadata\[\].value

</td>
<td valign="top">

array of strings

</td>
<td valign="top">

Yes \(if parent used\)

</td>
<td valign="top">

Acceptable values for the key

</td>
<td valign="top">

maxLength per item: 1024

</td>
</tr>
<tr>
<td valign="top">

filters\[\].documentMetadata\[\].matchMode

</td>
<td valign="top">

string

</td>
<td valign="top">

No

</td>
<td valign="top">

Matching mode for document metadata values

</td>
<td valign="top">

"ANY" or "ALL"

</td>
</tr>
<tr>
<td valign="top">

filters\[\].documentMetadata\[\].selectMode

</td>
<td valign="top">

array

</td>
<td valign="top">

No

</td>
<td valign="top">

Selection mode options

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

filters\[\].documentMetadata\[\].selectMode\[\]

</td>
<td valign="top">

string

</td>
<td valign="top">

No

</td>
<td valign="top">

Selection mode option

</td>
<td valign="top">

"ignoreIfKeyAbsent"

</td>
</tr>
<tr>
<td valign="top">

filters\[\].chunkMetadata

</td>
<td valign="top">

array

</td>
<td valign="top">

No

</td>
<td valign="top">

Metadata filters for chunks

</td>
<td valign="top">

maxItems: 2000

</td>
</tr>
<tr>
<td valign="top">

filters\[\].chunkMetadata\[\].key

</td>
<td valign="top">

string

</td>
<td valign="top">

Yes \(if parent used\)

</td>
<td valign="top">

Chunk metadata key to filter on

</td>
<td valign="top">

maxLength: 1024

</td>
</tr>
<tr>
<td valign="top">

filters\[\].chunkMetadata\[\].value

</td>
<td valign="top">

array of strings

</td>
<td valign="top">

Yes \(if parent used\)

</td>
<td valign="top">

Acceptable values for the key

</td>
<td valign="top">

maxLength per item: 1024

</td>
</tr>
</table>

