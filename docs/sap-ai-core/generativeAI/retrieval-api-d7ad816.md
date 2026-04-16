<!-- copyd7ad816f8432449c82f36e367abf82ba -->

# Retrieval API

The Retrieval API lets you retrieve repositories or collections created through the Vector API. It also lets you perform similarity searches on the vector database to obtain relevant chunks and documents.



<a name="copyd7ad816f8432449c82f36e367abf82ba__section_jcr_q5z_ydc"/>

## Prerequisites

You have created a vector database. For more information, see [Vector API](vector-api-08e3d00.md).



## Capacity Quotas and Input Limits



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



<a name="copyd7ad816f8432449c82f36e367abf82ba__section_dxk_glv_vfc"/>

## API Request Format

When you build your API requests, follow the format outlined in the *Retrieval* section of the Grounding API. For more information, see [Grounding API](https://api.sap.com/api/DOCUMENT_GROUNDING_API/resource/Retrieval).

-   **[Retrieve a List of All Data Repositories](retrieve-a-list-of-all-data-repositories-6a23d47.md "")**  

-   **[Retrieve a Specific Data Respository](retrieve-a-specific-data-respository-3be4a11.md "")**  

-   **[Retrieval Search](retrieval-search-9f731a3.md)**  


