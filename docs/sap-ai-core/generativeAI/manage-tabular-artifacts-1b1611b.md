<!-- loio1b1611b26e0945a4902e8dd3b54470b6 -->

# Manage Tabular Artifacts

Manage tabular artifacts for use in scenario configurations.

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

`/tabularArtifacts`

</td>
<td valign="top">

List all tabular artifacts

</td>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

`/tabularArtifacts/{name}`

</td>
<td valign="top">

Get details and full schema metadata

</td>
</tr>
<tr>
<td valign="top">

DELETE

</td>
<td valign="top">

`/tabularArtifacts/{name}`

</td>
<td valign="top">

Delete \(async soft-delete, returns 202\)

</td>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

`/tabularArtifacts/{name}/data`

</td>
<td valign="top">

Preview first 10 rows from the virtual table

</td>
</tr>
</table>



## List Tabular Artifacts

To list tabular artifacts, send a GET request to the endpoint:

```
curl -X GET "$AI_API_URL/v2/tcr/tabularArtifacts?\$top=20&\$count=true" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **200** and item details.

```
{
  "count": 2,
  "resources": [
    {
      "id": "ta-uuid-1234-5678-abcd-ef12",
      "name": "customer-data-ta",
      "tenantId": "tenant-abc123",
      "resourceGroupId": "my-resource-group",
      "dataDestinationName": "s3-training-data",
      "virtualTableName": "VT_CUSTOMER_DATA_TA_A1B2C3",
      "remoteSourceName": "RS_S3_TRAINING_DATA",
      "path": "/data/customers/customers_2024.csv",
      "type": "CSV",
      "status": "ACTIVE",
      "createdAt": "2024-03-12T08:00:00.000Z",
      "updatedAt": "2024-03-12T08:02:30.000Z"
    },
    {
      "id": "ta-uuid-9876-5432-efgh-ab34",
      "name": "sales-data-ta",
      "tenantId": "tenant-abc123",
      "resourceGroupId": "my-resource-group",
      "dataDestinationName": "hdl-production",
      "virtualTableName": null,
      "remoteSourceName": null,
      "path": "/data/sales/sales_q1.csv",
      "type": "CSV",
      "status": "PROCESSING",
      "createdAt": "2024-03-12T10:00:00.000Z",
      "updatedAt": "2024-03-12T10:00:00.000Z"
    }
  ]
}
```



## Retrieve a Tabular Artifact

To retrieve a tabular artifact, send a GET request to the endpoint:

```
curl -X GET "$AI_API_URL/v2/tcr/tabularArtifacts/customer-data-ta" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **200** and item details.

The response includes `status` details. If your `status` is `ACTIVE`, you'll receive the response below:

```
{
  "id": "ta-uuid-1234-5678-abcd-ef12",
  "name": "customer-data-ta",
  "tenantId": "tenant-abc123",
  "resourceGroupId": "my-resource-group",
  "dataDestinationName": "s3-training-data",
  "virtualTableName": "VT_CUSTOMER_DATA_TA_A1B2C3",
  "remoteSourceName": "RS_S3_TRAINING_DATA",
  "path": "/data/customers/customers_2024.csv",
  "type": "CSV",
  "status": "ACTIVE",
  "csnMetadata": {
    "entityName": "CustomerEntity",
    "selectedColumns": ["customer_id", "name", "purchase_amount", "region"],
    "definition": {
      "definitionType": "DOCUMENT",
      "document": { "...": "..." }
    }
  },
  "metadata": [
    {
      "type": "csn",
      "columns": [
        { "name": "customer_id",     "cdsType": "cds.String",  "length": 50 },
        { "name": "name",            "cdsType": "cds.String",  "length": 200 },
        { "name": "purchase_amount", "cdsType": "cds.Decimal", "precision": 15, "scale": 2 },
        { "name": "region",          "cdsType": "cds.String",  "length": 50 }
      ]
    }
  ],
  "createdAt": "2024-03-12T08:00:00.000Z",
  "updatedAt": "2024-03-12T08:02:30.000Z"
}
```

If your `status` is `PROCESSING`, you'll receive the response below:

```
{
  "id": "ta-uuid-9876-5432-efgh-ab34",
  "name": "sales-data-ta",
  "tenantId": "tenant-abc123",
  "resourceGroupId": "my-resource-group",
  "dataDestinationName": "hdl-production",
  "virtualTableName": null,
  "remoteSourceName": null,
  "path": "/data/sales/sales_q1.csv",
  "type": "CSV",
  "status": "PROCESSING",
  "csnMetadata": null,
  "metadata": null,
  "createdAt": "2024-03-12T10:00:00.000Z",
  "updatedAt": "2024-03-12T10:00:00.000Z"
}
```

Error responses return code **404**: Artifact not found.



## Delete a Tabular Artifact

This endpoint soft-deletes the artifact. The virtual table and remote source are dropped asynchronously.

```
curl -X DELETE "$AI_API_URL/v2/tcr/tabularArtifacts/sales-data-ta" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **202**.

**Error Responses**

-   **409:** Artifact is currently referenced by an active scenario configuration

-   **404:** Artifact not found




## Preview Data from a Tabular AI Artifact

Returns the first 10 rows from the virtual table. The artifact must have `status`: `ACTIVE`.

```
curl -X GET "$AI_API_URL/v2/tcr/tabularArtifacts/customer-data-ta/data" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **200** and item details.

```
{
  "name": "customer-data-ta",
  "columns": ["customer_id", "name", "purchase_amount", "region"],
  "data": [
    {
      "customer_id": "C-001",
      "name": "Acme Corporation",
      "purchase_amount": 15200.50,
      "region": "EMEA"
    },
    {
      "customer_id": "C-002",
      "name": "Globex Industries",
      "purchase_amount": 8750.00,
      "region": "NA"
    }
  ]
}
```

