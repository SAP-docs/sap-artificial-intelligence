<!-- loio12dd0b74b57c4b7eb1303bfa4c61b766 -->

# Scenario Configuration

A scenario configuration binds one or more tabular artifacts to a context selection strategy. This is the identifier your application passes to the Tabular AI Orchestration inference endpoint.

The following context selection strategies are available:


<table>
<tr>
<th valign="top">

Strategy

</th>
<th valign="top">

Description

</th>
<th valign="top">

When to use

</th>
</tr>
<tr>
<td valign="top">

`embedding`

</td>
<td valign="top">

Selects rows semantically similar to the query using vector embeddings

</td>
<td valign="top">

Production — when accuracy matters

</td>
</tr>
<tr>
<td valign="top">

`random`

</td>
<td valign="top">

Selects rows at random

</td>
<td valign="top">

Baseline testing and development

</td>
</tr>
</table>



## Create A Scenario Configuration with a Single Artifact

```
curl -X POST "$BASE_URL/scenarioConfigurations" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "customer-churn-scenario",
    "description": "Customer churn prediction using embedding-based context selection",
    "contextSelectionStrategy": "embedding",
    "tabularArtifacts": [
      { "name": "customer-data-ta" }
    ],
    "labels": [
      { "key": "ext.ai.sap.com/environment", "value": "production" },
      { "key": "ext.ai.sap.com/usecase", "value": "churn-prediction" }
    ]
  }'

```

> ### Output Code:  
> ```
> {
>   "name": "customer-churn-scenario"
> }
> 
> ```



## Create A Scenario Configuration with Multiple artifacts

A scenario can reference multiple Tabular Artifacts if the use case spans more than one table or file.

```
curl -X POST "$BASE_URL/scenarioConfigurations" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "sales-forecast-scenario",
    "contextSelectionStrategy": "random",
    "tabularArtifacts": [
      { "name": "sales-data-ta" },
      { "name": "orders-parquet-ta" }
    ]
  }'

```

> ### Output Code:  
> ```
> {
>   "name": "sales-forecast-scenario"
> }
> 
> ```



## Error Responses:

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

Invalid payload or referenced artifact does not exist

</td>
</tr>
<tr>
<td valign="top">

409

</td>
<td valign="top">

A scenario configuration with this name already exists

</td>
</tr>
</table>

-   **[Manage Scenario Configurations](manage-scenario-configurations-08068d9.md)**  


