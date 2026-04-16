<!-- copyfa7964aae7b44ef19073bf31391d8517 -->

# Preparing Data Using the Vector API

Vector API is a microservice provided with a Rest API and endpoints for creating and managing collection and documents.



<a name="copyfa7964aae7b44ef19073bf31391d8517__section_jcr_q5z_ydc"/>

## Prerequisites

You have created a resource group for grounding purposes. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).



To insert your document chunks into the vector store, you will need to follow the following operations:

1.  Create a collection For more information see [Create a Collection](create-a-collection-c124fb9.md).

2.  Insert documents and chunks into the collection. For more information see [Create a Document](create-a-document-11348e9.md).




<a name="copyfa7964aae7b44ef19073bf31391d8517__section_dxk_glv_vfc"/>

## API Request Format

When you build your API requests, follow the format outlined in the *Vector* section of the Grounding API. For more information, see [Grounding API](https://api.sap.com/api/DOCUMENT_GROUNDING_API/resource/Vector).

> ### Caution:  
> Do not expose personally identifiable or privileged information in your documents or chunks when using generative AI hub. Personally identifiable information is any data that can be used alone, or in combination, to identify the person that the data refers to. The document grounding capability has no mechanism for determining the type of data that it processes, and does not filter confidential or other privileged information.



<a name="copyfa7964aae7b44ef19073bf31391d8517__section_vyr_bqc_fgc"/>

## Next Steps

After preparing your vectors, you can use the Retrieval API for chunks relevant to a query, or use the grounding module as part of an orchestration workflow for information retrieval and LLM interaction. For more information, see [Retrieval API](retrieval-api-281e8cf.md) or [Using the Grounding Module](using-the-grounding-module-e1c4dd1.md).

Alternatively, you can search specific collections using vector search. For more information, see [Vector Search](vector-search-255589a.md)

