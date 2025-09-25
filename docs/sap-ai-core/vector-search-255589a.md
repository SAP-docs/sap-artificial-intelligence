<!-- loio255589ab034e4c1394ddf9498cf58dce -->

# Vector Search

This endpoint allows you to perform a search for relevant chunks within a specific collection or across all collections based on a user query. The response includes chunks that match the query, filtered by collection and document metadata.



## Procedure

Send a: POST request to the endpoint: `$AI_API_URL/v2/lm/document-grounding/vector/search`

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

Value

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

Enter “\*” to search all collections or add a collectionId to search a specific collection. To search more than one specific collection, add collectionIds in a comma separated list

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

 

<a name="loio255589ab034e4c1394ddf9498cf58dce__result_a34_n22_wfc"/>

## Results

The response is returned in JSON format, and includes relevant chunks based on similarity search..

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

