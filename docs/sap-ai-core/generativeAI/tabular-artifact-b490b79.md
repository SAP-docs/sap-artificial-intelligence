<!-- loiob490b79214fc40fc8bf5ebe9f97a5655 -->

# Tabular Artifact

A tabular artifact represents a specific file on a Data Destination that has been onboarded into the context registry.

Onboarding a tabular artifact consists of the following:

1.  Reads the CSN schema definition \(inline, by file reference, or auto-derived\)
2.  Creates a **virtual table** in SAP HANA pointing to the file
3.  Makes the data queryable at runtime for context selection

> ### Note:  
> Creation is **asynchronous**. The API returns `202 Accepted` immediately. Poll `GET /tabularArtifacts/{name}` until `status` is `READY` before using the artifact in a Scenario Configuration.



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

`READY`

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



## Examples



### DOCUMENT Method

Use the DOCUMENT method to embed the Core Schema Notation \(CSN\) JSON directly in the request.

```

curl -X POST "$BASE_URL/tabularArtifacts" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "customer-data-ta",
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
curl -X POST "$BASE_URL/tabularArtifacts" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "orders-parquet-ta",
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
curl -X POST "$BASE_URL/tabularArtifacts" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "sales-data-ta",
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

-   **[Manage Tabular Artifacts](manage-tabular-artifacts-1b1611b.md)**  


