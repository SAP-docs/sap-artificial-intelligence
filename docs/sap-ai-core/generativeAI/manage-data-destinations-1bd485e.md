<!-- loio1bd485eb10354753a8071b4f3d8f6ac3 -->

# Manage Data Destinations

The service provides APIs to **retrieve**, **list**, **update**, and **search** data destinations.



## List Data Destinations

Send a GET request to list all data destinations:

```
curl GET "$AI_API_URL/v2/tcr/dataDestinations" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN"
```

Successful responses return code **200** and item details.

```
{
  "count": 2,
  "resources": [
    {
      "name": "hdl-production",
      "type": "HDL",
      "description": "Production HANA Data Lake file container",
      "adapterType": "File",
      "labels": [
        { "key": "ext.ai.sap.com/environment", "value": "production" }
      ],
      "createdAt": "2024-03-10T09:00:00.000Z",
      "updatedAt": "2024-03-10T09:00:00.000Z"
    },
    {
      "name": "s3-training-data",
      "type": "S3",
      "description": "S3 bucket for training datasets",
      "adapterType": "File",
      "labels": [],
      "createdAt": "2024-03-11T11:30:00.000Z",
      "updatedAt": "2024-03-11T11:30:00.000Z"
    }
  ]
}
```



## Retrieve a Data Destination

Retrieve details of a specific data destination by sending a GET request to the following endpoint:

```
curl GET "$AI_API_URL/v2/tcr/dataDestinations /{dataDestinationName}" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN"
```

Successful responses return code **200** and item details.

```
{
  "name": "hdl-production",
  "type": "HDL",
  "description": "Production HANA Data Lake file container",
  "adapterType": "File",
  "labels": [
    { "key": "ext.ai.sap.com/environment", "value": "production" }
  ],
  "createdAt": "2024-03-10T09:00:00.000Z",
  "updatedAt": "2024-03-10T09:00:00.000Z"
}
```



## Update a Data Destinations

You can update the `labels`, `description`, and or `config` \(credentials\) fields. The `name` and `type` fields cannot be changed after creation.

The patchable credential field per type:


<table>
<tr>
<th valign="top">

Type

</th>
<th valign="top">

Patchable credential field\(s\)

</th>
</tr>
<tr>
<td valign="top">

S3

</td>
<td valign="top">

`access_key_id`, `secret_access_key` 

</td>
</tr>
<tr>
<td valign="top">

GCS

</td>
<td valign="top">

`base64_encoded_private_key_data` 

</td>
</tr>
<tr>
<td valign="top">

AZURE

</td>
<td valign="top">

`sas_token` 

</td>
</tr>
<tr>
<td valign="top">

HDL

</td>
<td valign="top">

Not patchable

</td>
</tr>
</table>

Send a PATCH request to update metadata labels for a data destination:

```
curl -X PATCH "$BASE_URL/dataDestinations/s3-training-data" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "description": "Updated S3 bucket for ML training datasets",
    "labels": [
      { "key": "ext.ai.sap.com/environment", "value": "staging" }
    ],
    "config": {
      "access_key_id": "AKIANEWKEYEXAMPLE123",
      "secret_access_key": "newSecretKeyValue/Example+Key"
    }
  }'
```

Successful responses return code **204**.

**Error Responses**

-   **400:** Invalid payload or label format violation

-   **404:** Data destination not found




## Delete Data Destinations

Send a DELETE request to the following endpoint:

```
curl -X DELETE "$BASE_URL/dataDestinations/s3-training-data" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **204**.

**Error Responses**

-   **409:** Data destination has active dependencies that block deletion

-   **404:** Data destination not found




## Search Data Destinations

To filter destinations by metadata labels, use the search API:

```
curl -X POST "$BASE_URL/dataDestinations/search" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "labels": [
      { "key": "ext.ai.sap.com/environment", "value": "production" }
    ]
  }''
```

Successful responses return code **200** and item details.

Entries are returned if they match all specified labels \(AND logic\).

```
{
  "count": 1,
  "resources": [
    {
      "name": "hdl-production",
      "type": "HDL",
      "description": "Production HANA Data Lake file container",
      "adapterType": "File",
      "labels": [
        { "key": "ext.ai.sap.com/environment", "value": "production" }
      ],
      "createdAt": "2024-03-10T09:00:00.000Z",
      "updatedAt": "2024-03-10T09:00:00.000Z"
    }
  ]
}
```



## Validate a New Data Destination

You can test provider connectivity without persisting anything, to verify credentials and access before creation.

```
curl -X POST "$BASE_URL/dataDestinations/validate" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "type": "S3",
    "config": {
      "bucket": "my-ml-training-bucket",
      "region": "eu-central-1",
      "access_key_id": "AKIAIOSFODNN7EXAMPLE",
      "secret_access_key": "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY"
    }
  }'
```

Successful responses return code **200** and `status`: `OK`.

Unsuccessful responses return code **200** and `status`: `FAILED`, as well as a reason.



## Validate an Existing Data Destination

You can retest provider connectivity, for example after patching your credentials.

```
curl -X POST "$BASE_URL/dataDestinations/s3-training-data/validate" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **200** and `status`: `OK`.

Error Responses return code **404**: Data destination not found

