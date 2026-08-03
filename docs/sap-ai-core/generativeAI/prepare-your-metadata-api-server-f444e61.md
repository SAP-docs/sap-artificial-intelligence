<!-- copyf444e612fa224de196da726723d04df2 -->

# Prepare your Metadata API Server

The metadata server enables grounding to process documents from your repositories, enriched with metadata for improved contextualization. To incorporate metadata into grounding, you must prepare, deploy and host a metadata server. The **default** path is `/v1/dg-pipeline/metadata` and the HTTP method is GET.

For metadata servers hosted at the default path, you only need to specify the **base** URL, for example, https://metadata-server.com in the `URL` field of the generic secret.

For metadata servers not hosted at the default path, you need to specify the **full** URL, for example, https://metadata-server.com/custom/path/to/metadata in the `URL` field of the generic secret.



<a name="copyf444e612fa224de196da726723d04df2__section_hh5_h23_cgc"/>

## Metadata API Response Structure

Your metadata server must return a response in the following format:

> ### Output Code:  
> ```
> {
>   "documentsCount": 100,
>   "value": [
>     {
>       "metadata": [
>         {
>           "key": "domainId",
>           "value": ["PUBLIC", "PRIVATE"],
>           "matchMode": "ANY"
>         },
>         {
>           "key": "department",
>           "value": ["HR", "Finance", "Engineering"],
>           "matchMode": "ALL"
>         }
>       ],
>       "documents": [
>         {
>           "id": "3893fe5e-9b22-4eb3-ad12-6a8b4b38f25h",
>           "viewLocation": "/path/to/view/doc",
>           "metadata": [
>             {
>               "key": "domainId",
>               "value": ["PRIVATE"]
>             },
>             {
>               "key": "department",
>               "value": ["HR", "Finance"],
>               "matchMode": "ALL"
>             }
>           ],
>           "downloadLocation": "/path/to/download/doc",
>           "lastUpdatedTimestamp": "2024-02-25T12:00:00Z"
>         }
>         // ... more documents
>       ]
>     }
>     // ... more document groups
>   ]
> }
> ```

The top-level value is an array of document groups.

Each document group contains group-level `metadata` and a `documents` array.

Each document must have the following:

-   A unique `id`
-   `viewLocation`: the file location in the repository
-   `lastUpdatedTimestamp`: the timestamp of the last update

Optionally, documents can also have the following;

-   `metadata`: your choice of labels
-   `downloadLocation`: the location from that the file can be downloaded from

The metadata keys and values are your own meaningful custom strings.

`matchMode` must be `ALL` to match all metadata values, or `ANY` to match any single value.



### Authentication Requirements

Your metadata API must be secured using OAuth2ClientCredentials flow. You can use one of the following:

-   Client secret-based authentication

-   Mutual TLS \(mTLS\) with client certificates


For more information, see [Generic Secrets for Contextualization with Metadata](generic-secrets-for-contextualization-with-metadata-dade07e.md).

Ensure your server validates the incoming access token before serving the metadata.





### Pagination

Pagination is optional.

If pagination is included, the following query parameters must be supported:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`$top` 

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Max number of documents to return.

</td>
</tr>
<tr>
<td valign="top">

`$skip` 

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Number of documents to skip.

</td>
</tr>
<tr>
<td valign="top">

`$count` 

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

`true`: returns the total number of documents available on the server in the `documentsCount` field.

`false`: returns the number of documents included in the current response in the `documentsCount` field.

</td>
</tr>
</table>

**Pagination requirements** 

Pagination must be applied across all document groups, meaning the API returns`$top`, `$count` and skip the first `$skip` documents globally, regardless of which group they belong to.

Document groups with no documents must be removed from the response.

The API must not return more documents than specified by `$top`.

The generic secret for the metadata server can include a `pageSize` attribute to set`$top`. For more information, see [Generic Secrets for Contextualization with Metadata](generic-secrets-for-contextualization-with-metadata-dade07e.md)

> ### Example:  
> A GET request to the endpoint `GET <BASE_URL>/v1/dg-pipeline/metadata?$top=2&$skip=1&$count=true` should return the following response:
> 
> > ### Output Code:  
> > ```
> > {
> >   "documentsCount": 5, // Total documents available on server (since $count=true)
> >   "value": [
> >     {
> >       "metadata": [
> >         { "key": "domainId", "value": ["PUBLIC", "PRIVATE"], "matchMode": "ANY" },
> >         { "key": "department", "value": ["HR", "Finance", "Engineering"], "matchMode": "ALL" }
> >       ],
> >       "documents": [
> >         {
> >           "id": "doc-002-id",
> >           "viewLocation": "/path/to/view/doc2",
> >           "metadata": [
> >             { "key": "domainId", "value": ["PUBLIC"], "matchMode": "ANY" },
> >             { "key": "department", "value": ["HR", "Finance"], "matchMode": "ALL" }
> >           ],
> >           "downloadLocation": "/path/to/download/doc2",
> >           "lastUpdatedTimestamp": "2024-02-26T12:00:00Z"
> >         },
> >         {
> >           "id": "doc-003-id",
> >           "viewLocation": "/path/to/view/doc3",
> >           "metadata": [
> >             { "key": "domainId", "value": ["PRIVATE"]}
> >           ],
> >           "downloadLocation": "/path/to/download/doc3",
> >           "lastUpdatedTimestamp": "2024-02-27T12:00:00Z"
> >         }
> >       ]
> >     }
> >   ]
> > }
> > ```



<a name="copyf444e612fa224de196da726723d04df2__section_ubb_db3_cgc"/>

## Deployment

Now that you've prepared your application, you can deploy it. For more information, see [SAP BTP Deploy an Application](https://help.sap.com/docs/btp/sap-business-technology-platform/deploy-application?locale=en-US), [DAP BTP Deploying to the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/deploying-to-cloud-foundry-environment) and [Create an Application with Cloud Foundry Python Buildpack BTP Tutorial](https://developers.sap.com/tutorials/btp-cf-buildpacks-python-create.html).

