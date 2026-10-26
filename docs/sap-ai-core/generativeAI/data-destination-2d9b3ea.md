<!-- loio2d9b3ea500d549c8a65aeb83f4b12eb8 -->

# Data Destination

A Data Destination represents a connection to an external storage system. It encapsulates connection credentials so that downstream components never handle them directly.

Every Tabular Artifact must reference a Data Destination.

The following types are supported:


<table>
<tr>
<th valign="top">

Type

</th>
<th valign="top">

Storage System

</th>
</tr>
<tr>
<td valign="top">

`HDL`

</td>
<td valign="top">

SAP HANA Data Lake Files

</td>
</tr>
<tr>
<td valign="top">

`S3`

</td>
<td valign="top">

Amazon S3

</td>
</tr>
<tr>
<td valign="top">

`GCS`

</td>
<td valign="top">

Google Cloud Storage

</td>
</tr>
<tr>
<td valign="top">

`AZURE`

</td>
<td valign="top">

Azure Blob Storage \(ADLS Gen2\)

</td>
</tr>
</table>



## Create a Data Destination

> ### Note:  
> Data destination creation is asynchronous. The service immediately accepts the request and returns `202 Accepted` while credential validation and secret storage are processed in the background. Credentials are stored securely and are not returned in `GET` or `LIST` responses.
> 
> Before creating a tabular artifact, retrieve the data destination and verify that its status is `ACTIVE`. If creation fails, the destination status is `ERROR`, and the `errorMessage` field provides details about the failure. To retry the operation, send another `PUT` request with the same destination name.
> 
> Specify the destination name in the request path, not in the request body.

**Query Parameters**


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
<th valign="top">

Applicable To

</th>
</tr>
<tr>
<td valign="top">

`namedSp`

</td>
<td valign="top">

boolean

</td>
<td valign="top">

When set to `true`, returns HDL subject patterns in the `namedSubjectPatterns` object in addition to `subjectPatterns`.

</td>
<td valign="top">

HDL data destinations \(PUT endpoints\)

</td>
</tr>
</table>

Use the `subjectPatterns` values returned in the HDL response to configure mTLS trust on the SAP HANA Data Lake side.

Use the following API to register your data destination by sending a PUT request to the endpoint: `$AI_API_URL/v2/tcr/dataDestinations/``<name>`

**Endpoint**


<table>
<tr>
<th valign="top">

Method

</th>
<th valign="top">

Path

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

PUT

</td>
<td valign="top">

`/dataDestinations/{name}`

</td>
<td valign="top">

Create or retry a data destination asynchronously

</td>
</tr>
</table>



## HDL

Populate the following with your details:

```
curl PUT -X "$AI_API_URL/v2/tcr/dataDestinations/hdl-production" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
  "type": "HDL",
  "description": "HDL data destination for payment prediction use case",
  "adapterType": "File",
  "config": {
    "host": "<your-container-id>.files.hdl.<region>.hanacloud.ondemand.com"
  }
}'
```

> ### Note:  
> The data destination name must contain only lowercase alphanumeric characters and hyphens. The host value corresponds to the HANA Data Lake container endpoint available in the SAP BTP subaccount.



### Results

A successful request returns HTTP status code `202 Accepted` along with the generated mTLS subject patterns.

> ### Output Code:  
> ```
> {
>   "name": "hdl-production",
>   "subjectPatterns": [
>     "sap.ai.core:resourceGroup:my-resource-group:dataDestination:hdl-production"
>   ]
> }
> ```



## AWS

Populate the following with your details:

```
curl PUT -X "$AI_API_URL/v2/tcr/dataDestinations/s3-training-data" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "type": "S3",
    "description": "S3 bucket for training datasets",
    "config": {
      "bucket": "my-ml-training-bucket",
      "region": "eu-central-1",
      "access_key_id": "AKIAIOSFODNN7EXAMPLE",
      "secret_access_key": "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY"
    }
  }'
```

> ### Output Code:  
> ```
> Response — 202 Accepted:
> {
>   "name": "s3-training-data"
> }
> ```



## GCS

Populate the following with your details.

The `base64_encoded_private_key_data` is the full service account JSON key, base64-encoded, which is the same value provided by the BTP Object Store service key:

```
curl PUT -X "$AI_API_URL/v2/tcr/dataDestinations/gcs-analytics" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "type": "GCS",
    "config": {
      "bucket": "my-gcs-analytics-bucket",
      "base64_encoded_private_key_data": "eyJjbGllbnRfZW1haWwiOiJzZXJ2aWNlQGV4YW1wbGUuaWFtLmdzZXJ2aWNlYWNjb3VudC5jb20iLCJwcml2YXRlX2tleSI6Ii0tLS0tQkVHSU4gUFJJVkFURSBLRVktLS0tLVxuLi4uXG4tLS0tLUVORCBQUklWQVRFIEtFWS0tLS0tIn0="
    }
  }'
```

> ### Output Code:  
> ```
> Response — 202 Accepted:
> {
>   "name": "gcs-analytics"
> }
> ```



## Azure

Populate the following with your details:

```
curl PUT -X "$AI_API_URL/v2/tcr/dataDestinations/azure-blob-store" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "type": "AZURE",
    "config": {
      "account_name": "mystorageaccount",
      "container_uri": "https://mystorageaccount.z2.blob.storage.azure.net/mycontainer",
      "sas_token": "sv=2023-01-03&ss=b&srt=sco&sp=rl&se=2025-12-31T00:00:00Z&st=2024-01-01T00:00:00Z&spr=https&sig=EXAMPLE_SIG"
    }
  }'
```

> ### Output Code:  
> ```
> Response — 202 Accepted:
> {
>   "name": "azure-blob-store"
> }
> ```



## Error Responses

The results may include the following error responses:


<table>
<tr>
<th valign="top">

Status

</th>
<th valign="top">

When

</th>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Missing required fields, name pattern violation, or invalid `host` format

</td>
</tr>
<tr>
<td valign="top">

409

</td>
<td valign="top">

A data destination with this name already exists in the resource group

</td>
</tr>
<tr>
<td valign="top">

500

</td>
<td valign="top">

Connectivity validation failed or internal error

</td>
</tr>
</table>



## Next Step

> ### Note:  
> Creating a data destination is an asynchronous operation. The service immediately accepts the request and returns `202 Accepted`, while credential validation and secret storage are processed in the background. Credentials are stored securely and aren't included in GET or LIST responses.

Before creating a tabular artifact, poll `GET /dataDestinations/{name}` until the data destination status changes to `ACTIVE`.

If the operation fails, the data destination status changes to `ERROR`. The response includes an `errorMessage` field that describes the reason for the failure.

To retry the operation, send another PUT request with the same data destination name.

For more information about retrieving a data destination status, see [Retrieve Destination](https://help.sap.com/docs/AI_CORE/7d01240443d84db6890f318fe5d1123f/1bd485eb10354753a8071b4f3d8f6ac3.html?locale=en-US&state=DRAFT&version=DEV).

-   **[Manage Data Destinations](manage-data-destinations-1bd485e.md)**  


