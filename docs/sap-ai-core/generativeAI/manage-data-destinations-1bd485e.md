<!-- loio1bd485eb10354753a8071b4f3d8f6ac3 -->

# Manage Data Destinations

The service provides APIs to **retrieve**, **list**, **update**, and **search** data destinations.

**Endpoints**


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

GET

</td>
<td valign="top">

`/dataDestinations`

</td>
<td valign="top">

List all data destinations

</td>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

`/dataDestinations/{name}`

</td>
<td valign="top">

Get details \(credentials excluded\)

</td>
</tr>
<tr>
<td valign="top">

PATCH

</td>
<td valign="top">

`/dataDestinations/{name}`

</td>
<td valign="top">

Update labels, description, or credentials

</td>
</tr>
<tr>
<td valign="top">

DELETE

</td>
<td valign="top">

`/dataDestinations/{name}`

</td>
<td valign="top">

Mark for asynchronous deletion

</td>
</tr>
<tr>
<td valign="top">

POST

</td>
<td valign="top">

`/dataDestinations/search`

</td>
<td valign="top">

Search by label key-value pairs

</td>
</tr>
<tr>
<td valign="top">

POST

</td>
<td valign="top">

`/dataDestinations/validate`

</td>
<td valign="top">

Test connectivity before creating

</td>
</tr>
<tr>
<td valign="top">

POST

</td>
<td valign="top">

`/dataDestinations/{name}/validate`

</td>
<td valign="top">

Re-verify an existing destination

</td>
</tr>
</table>

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

HDL data destinations \(GET endpoints\)

</td>
</tr>
</table>



## List Data Destinations

Send a GET request to list all data destinations:

```
curl GET "$AI_API_URL/v2/tcr/dataDestinations?\$top=10&\$count=true" \
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
      "status": "ACTIVE",
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
      "status": "ACTIVE",
      "labels": [],
      "createdAt": "2024-03-11T11:30:00.000Z",
      "updatedAt": "2024-03-11T11:30:00.000Z"
    }
  ]
}
  ]
}
```



## Retrieve a Data Destination

Retrieve details of a specific data destination by sending a GET request to the following endpoint:

```
curl GET "$AI_API_URL/v2/tcr/dataDestinations/hdl-production" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN"
```

Successful responses return code **200** and item details.

The destination status can be ACTIVE, PROCESSING, or ERROR.

```
{
  "name": "hdl-production",
  "type": "HDL",
  "description": "Production HANA Data Lake file container",
  "adapterType": "File",
  "status": "ACTIVE",
  "labels": [
    { "key": "ext.ai.sap.com/environment", "value": "production" }
  ],
  "createdAt": "2024-03-10T09:00:00.000Z",
  "updatedAt": "2024-03-10T09:00:00.000Z"
}
```

```
{
  "name": "hdl-production",
  "type": "HDL",
  "description": "Production HANA Data Lake file container",
  "adapterType": "File",
  "status": "PROCESSING",
  "labels": [
    { "key": "ext.ai.sap.com/environment", "value": "production" }
  ],
  "createdAt": "2024-03-10T09:00:00.000Z",
  "updatedAt": "2024-03-10T09:00:00.000Z"
}
```

```
{
  "name": "hdl-production",
  "type": "HDL",
  "description": "Production HANA Data Lake file container",
  "adapterType": "File",
  "status": "ERROR",
  "errorMessage": "Failed to validate credentials: Access denied to HDL endpoint",
  "labels": [
    { "key": "ext.ai.sap.com/environment", "value": "production" }
  ],
  "createdAt": "2024-03-10T09:00:00.000Z",
  "updatedAt": "2024-03-10T09:00:00.000Z"
}
```

Successful responses return code **200** and item details.



### Retrieve Named Subject Patterns

To include named subject patterns in the response, set the `namedSp` query parameter to `true`.

```

curl -X GET "$AI_API_URL/v2/tcr/dataDestinations/hdl-production?namedSp=true" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"

```

The response contains the `subjectPatterns` array and the `namedSubjectPatterns` object.

```

{
  "name": "hdl-production",
  "type": "HDL",
  "status": "ACTIVE",
  "subjectPatterns": [
    "sap.ai.core:resourceGroup:my-resource-group:dataDestination:hdl-production"
  ],
  "namedSubjectPatterns": {
    "hanaSubjectPattern": "sap.ai.core:resourceGroup:my-resource-group:dataDestination:hdl-production",
    "aciorePklSubjectPattern": "sap.ai.core:resourceGroup:my-resource-group:dataDestination:hdl-production"
  },
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
curl -X PATCH "$AI_API_URL/v2/tcr/dataDestinations/s3-training-data" \
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
curl -X DELETE "$AI_API_URL/v2/tcr/dataDestinations/s3-training-data" \
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
curl -X POST "$AI_API_URL/v2/tcr/dataDestinations/search" \
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
curl -X POST "$AI_API_URL/v2/tcr/dataDestinations/validate" \
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
curl -X POST "$AI_API_URL/v2/tcr/dataDestinations/s3-training-data/validate" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **200** and `status`: `OK`.

Error Responses return code **404**: Data destination not found

