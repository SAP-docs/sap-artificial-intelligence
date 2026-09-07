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

For more information on configuring SAP HANA Data Lake connectivity, see [HANA Data Connectivity GitHub](https://github.tools.sap/AI/context-registry/blob/main/docs/blog/subject_pattern_hdl.md).

Use the following API to register your data destination by sending a PUT request to the endpoint: `$BASE_URL/dataDestinations/``<name>`



## HDL

Populate the following with your details:

```
curl PUT -X "$BASE_URL/dataDestinations/hdl-production" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
  "name": "my-hdl-destination",
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

A successful request returns HTTP status code `201 Created` along with the generated mTLS subject patterns.

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
curl PUT -X "$BASE_URL/dataDestinations/s3-training-data" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "name": "s3-training-data",
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



### Results

A successful request returns HTTP status code `201 Created`.

> ### Output Code:  
> ```
> {
>   "name": "s3-training-data"
> }
> ```



## GCS

Populate the following with your details.

The `base64_encoded_private_key_data` is the full service account JSON key, base64-encoded, which is the same value provided by the BTP Object Store service key.:

```
curl PUT -X "$BASE_URL/dataDestinations/gcs-analytics" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "name": "gcs-analytics",
    "type": "GCS",
    "config": {
      "bucket": "my-gcs-analytics-bucket",
      "base64_encoded_private_key_data": "eyJjbGllbnRfZW1haWwiOiJzZXJ2aWNlQGV4YW1wbGUuaWFtLmdzZXJ2aWNlYWNjb3VudC5jb20iLCJwcml2YXRlX2tleSI6Ii0tLS0tQkVHSU4gUFJJVkFURSBLRVktLS0tLVxuLi4uXG4tLS0tLUVORCBQUklWQVRFIEtFWS0tLS0tIn0="
    }
  }'
```



### Results

A successful request returns HTTP status code `201 Created`.

> ### Output Code:  
> ```
> {
>   "name": "gcs-analytics"
> }
> ```



## Azure

Populate the following with your details:

```
curl PUT -X "$BASE_URL/dataDestinations/azure-blob-store" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "name": "azure-blob-store",
    "type": "AZURE",
    "config": {
      "account_name": "mystorageaccount",
      "container_uri": "https://mystorageaccount.z2.blob.storage.azure.net/mycontainer",
      "sas_token": "sv=2023-01-03&ss=b&srt=sco&sp=rl&se=2025-12-31T00:00:00Z&st=2024-01-01T00:00:00Z&spr=https&sig=EXAMPLE_SIG"
    }
  }'
```



### Results

A successful request returns HTTP status code `201 Created`.

> ### Output Code:  
> ```
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

-   **[Manage Data Destinations](manage-data-destinations-1bd485e.md)**  


