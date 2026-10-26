<!-- loio08068d97f8b845ffa3ff92586021ee0e -->

# Manage Scenario Configurations

Manage scenario configurations that define the settings and parameters required for AI scenarios.

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

`/scenarioConfigurations`

</td>
<td valign="top">

List all scenario configurations

</td>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

`/scenarioConfigurations/{name}`

</td>
<td valign="top">

Get details of a specific configuration

</td>
</tr>
<tr>
<td valign="top">

PATCH

</td>
<td valign="top">

`/scenarioConfigurations/{name}`

</td>
<td valign="top">

Update strategy, artifacts, labels, or description

</td>
</tr>
<tr>
<td valign="top">

DELETE

</td>
<td valign="top">

`/scenarioConfigurations/{name}`

</td>
<td valign="top">

Delete the configuration

</td>
</tr>
<tr>
<td valign="top">

POST

</td>
<td valign="top">

`/scenarioConfigurations/search`

</td>
<td valign="top">

Search by label key-value pairs

</td>
</tr>
</table>



## List Scenario Configurations

To list all scenario configurations in your resource group, send a GET request to the following endpoint:

```
curl GET "$AI_API_URL/v2/tcr/scenarioConfigurations"?\$top=10&\$count=true" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN"

```

Successful responses return code **200** and item details.

```
{
  "count": 2,
  "resources": [
    {
      "name": "customer-churn-scenario",
      "description": "Customer churn prediction using embedding-based context selection",
      "contextSelectionStrategy": "embedding",
      "tabularArtifacts": [
        { "name": "customer-data-ta" }
      ],
      "labels": [
        { "key": "ext.ai.sap.com/environment", "value": "production" }
      ],
      "status": "ACTIVE",
      "createdAt": "2024-03-13T10:00:00.000Z",
      "updatedAt": "2024-03-13T10:00:00.000Z"
    },
    {
      "name": "sales-forecast-scenario",
      "description": null,
      "contextSelectionStrategy": "random",
      "tabularArtifacts": [
        { "name": "sales-data-ta" },
        { "name": "orders-parquet-ta" }
      ],
      "labels": [],
      "status": "ACTIVE",
      "createdAt": "2024-03-13T11:00:00.000Z",
      "updatedAt": "2024-03-13T11:00:00.000Z"
    }
  ]
}
```



## Retrieve a Scenario Configuration

To retrieve a single scenario configuration, send a GET request to the following endpoint:

```
curl -X GET "$AI_API_URL/v2/tcr/scenarioConfigurations/customer-churn-scenario" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **200** and item details.

```
{
  "name": "customer-churn-scenario",
  "description": "Customer churn prediction using embedding-based context selection",
  "contextSelectionStrategy": "embedding",
  "tabularArtifacts": [
    { "name": "customer-data-ta" }
  ],
  "labels": [
    { "key": "ext.ai.sap.com/environment", "value": "production" },
    { "key": "ext.ai.sap.com/usecase", "value": "churn-prediction" }
  ],
  "status": "ACTIVE",
  "createdAt": "2024-03-13T10:00:00.000Z",
  "updatedAt": "2024-03-13T10:00:00.000Z"
}
```



## Update a Scenario Configuration

You can update any combination of the following: `contextSelectionStrategy`, `tabularArtifacts`, `labels`, or `description`. The `name` cannot be changed. At least one field must be present.

****Update Strategy****

```
curl -X PATCH "$AI_API_URL/v2/tcr/scenarioConfigurations/customer-churn-scenario" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "contextSelectionStrategy": "random"
  }'
```

**Replace Tabular Artifacts**

```
curl -X PATCH "$AI_API_URL/v2/tcr/scenarioConfigurations/customer-churn-scenario" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "tabularArtifacts": [
      { "name": "customer-data-ta" },
      { "name": "orders-parquet-ta" }
    ]
  }'
```

Successful responses return code **204**.

**Error Responses**

-   **400:** Invalid payload or label format violation

-   **404:** Scenario configuration not found




## Delete a Scenario Configuration

Send a DELETE request to the endpoint:

```
curl -X DELETE "$AI_API_URL/v2/tcr/scenarioConfigurations/customer-churn-scenario" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP"
```

Successful responses return code **204**.

Error responses return code **404**: Scenario configuration not found



## Search for a Configuration by Labels

Returns scenario configurations matching all specified labels \(AND logic\).

```
curl -X POST "$AI_API_URL/v2/tcr/scenarioConfigurations/search" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "labels": [
      { "key": "ext.ai.sap.com/environment", "value": "production" }
    ]
  }'
```

Successful responses return code **200** and item details.

```
{
  "count": 1,
  "resources": [
    {
      "name": "customer-churn-scenario",
      "description": "Customer churn prediction using embedding-based context selection",
      "contextSelectionStrategy": "embedding",
      "tabularArtifacts": [
        { "name": "customer-data-ta" }
      ],
      "labels": [
        { "key": "ext.ai.sap.com/environment", "value": "production" }
      ],
      "createdAt": "2024-03-13T10:00:00.000Z",
      "updatedAt": "2024-03-13T10:00:00.000Z"
    }
  ]
}
```

Successful responses with no matches return code **200** and empty item details.

```
{
  "count": 0,
  "resources": []
}
```

