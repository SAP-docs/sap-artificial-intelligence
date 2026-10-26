<!-- loiob490b79214fc40fc8bf5ebe9f97a5655 -->

# Tabular Artifact

A tabular artifact represents a specific file on a Data Destination that has been onboarded into the context registry.

Onboarding a tabular artifact consists of the following:

1.  Reads the Core Schema Notation \(CSN\) schema definition \(inline, by file reference, or auto-derived\).
2.  Creates a **virtual table** in SAP HANA pointing to the file.
3.  Makes the data queryable at runtime for context selection.



## CSN Schema Definition Types

You register a tabular artifact by using one of the following methods:


<table>
<tr>
<th valign="top">

`definitionType`

</th>
<th valign="top">

When to use

</th>
</tr>
<tr>
<td valign="top">

`DOCUMENT`

</td>
<td valign="top">

Embed the CSN schema inline in the request

</td>
</tr>
<tr>
<td valign="top">

`REFERENCE`

</td>
<td valign="top">

CSN schema file already lives on the data destination

</td>
</tr>
<tr>
<td valign="top">

`AUTO`

</td>
<td valign="top">

Let the system derive the schema from the file

</td>
</tr>
</table>



## Artifact Status Lifecycle

The artifact lifecycle consists of the following stages:


<table>
<tr>
<th valign="top">

Status

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`PROCESSING`

</td>
<td valign="top">

Asynchronous creation in progress

</td>
</tr>
<tr>
<td valign="top">

`ACTIVE`

</td>
<td valign="top">

Fully available — safe to reference in a Scenario Configuration

</td>
</tr>
<tr>
<td valign="top">

`ERROR`

</td>
<td valign="top">

Creation failed — check the artifact details

</td>
</tr>
<tr>
<td valign="top">

`DELETING`

</td>
<td valign="top">

Soft-deleted, awaiting async cleanup

</td>
</tr>
</table>



## Create a Tabular Artifact

> ### Note:  
> Tabular artifact creation is asynchronous. The request is accepted immediately and returns `202 Accepted`, while schema validation and resource creation run in a separate task.
> 
> Before you use the artifact in a scenario configuration, poll `GET /tabularArtifacts/{name}` until the artifact status is `ACTIVE`.
> 
> If creation fails, the artifact status is `ERROR` and the response includes an `errorMessage` field. To retry the operation, send another `PUT` request with the same artifact name.
> 
> Specify the artifact name in the request path. Do not include the name in the request body.

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

`/tabularArtifacts/{name}`

</td>
<td valign="top">

Create a new tabular artifact asynchronously \(returns 202\)

</td>
</tr>
</table>



## Examples



### DOCUMENT Method

Use the DOCUMENT method to embed the CSN JSON directly in the request.

```

curl -X PUT "$AI_API_URL/v2/tcr/tabularArtifacts/customer-data-ta" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "dataDestinationName": "s3-training-data",
    "type": "CSV",
    "path": "/data/customers/customers_2024.csv",
    "csnMetadata": {
      "entityName": "CustomerEntity",
      "selectedColumns": ["customer_id", "name", "purchase_amount", "region"],
      "definition": {
        "definitionType": "DOCUMENT",
        "document": {
          "namespace": "com.example",
          "definitions": {
            "CustomerEntity": {
              "kind": "entity",
              "elements": {
                "customer_id":      { "type": "cds.String",  "length": 50 },
                "name":             { "type": "cds.String",  "length": 200 },
                "purchase_amount":  { "type": "cds.Decimal", "precision": 15, "scale": 2 },
                "region":           { "type": "cds.String",  "length": 50 }
              }
            }
          }
        }
      }
    }
 }'
```

> ### Output Code:  
> ```
> Response — 202 Accepted:
> {
>   "name": "customer-data-ta"
> }
> ```



### REFERENCE Method

Use the REFERENCE method to reference a CSN file stored in the data source.

```
curl -X PUT "$AI_API_URL/v2/tcr/tabularArtifacts/orders-parquet-ta" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "dataDestinationName": "s3-training-data",
    "type": "PARQUET",
    "path": "/data/orders/orders_2024.parquet",
    "csnMetadata": {
      "entityName": "OrderEntity",
      "definition": {
        "definitionType": "REFERENCE",
        "documentReference": {
          "path": "/schemas/orders_csn.json"
        }
      }
    }
  }'
```

> ### Output Code:  
> ```
> Response — 202 Accepted:
> {
>   "name": "orders-parquet-ta"
> }
> ```



### AUTO Method

Use the AUTO method to automatically discover schema metadata from the source.

```
curl -X PUT "$AI_API_URL/v2/tcr/tabularArtifacts/sales-data-ta" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "dataDestinationName": "hdl-production",
    "type": "CSV",
    "path": "/data/sales/sales_q1.csv",
    "csnMetadata": {
      "definition": {
        "definitionType": "AUTO",
        "autoConfig": {
          "csvOptions": {
            "columnListInFirstRow": true,
            "delimiter": ","
          }
        }
 }'
```

> ### Output Code:  
> ```
> Response — 202 Accepted:
> {
>   "name": "sales-data-ta"
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

Invalid payload, `path` does not start with `/`, or unsupported `type`

</td>
</tr>
<tr>
<td valign="top">

409

</td>
<td valign="top">

A tabular artifact with this name already exists

</td>
</tr>
</table>



## Next Step

For more information about tabular artifact status, see [Retrieve a tabular artifact](https://help.sap.com/docs/AI_CORE/b9f48eb4a993445b863a55dd4d38f64d/1b1611b26e0945a4902e8dd3b54470b6.html?locale=en-US&state=DRAFT&version=CLOUD).

-   **[Manage Tabular Artifacts](manage-tabular-artifacts-1b1611b.md)**  


