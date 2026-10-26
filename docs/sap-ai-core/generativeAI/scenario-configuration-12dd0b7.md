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

**Scenario Configuration Status Lifecycle**


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

Creation is running in the background

</td>
</tr>
<tr>
<td valign="top">

`ACTIVE`

</td>
<td valign="top">

Fully created and available for use

</td>
</tr>
<tr>
<td valign="top">

`ERROR`

</td>
<td valign="top">

Creation failed; inspect `errorMessage` and retry with `PUT` if appropriate

</td>
</tr>
<tr>
<td valign="top">

`DELETING`

</td>
<td valign="top">

Marked for deletion and awaiting asynchronous cleanup

</td>
</tr>
</table>



## Create Scenario Configuration

> ### Note:  
> Scenario configuration creation is asynchronous. The request is accepted immediately and returns `202 Accepted` while validation and background processing continue.
> 
> Poll `GET /scenarioConfigurations/{name}` until the scenario configuration reaches the `ACTIVE` status.
> 
> If creation fails, the scenario configuration status is set to `ERROR`, and an `errorMessage` is returned. To retry the operation, send another `PUT` request with the same scenario configuration name.
> 
> Specify the scenario configuration name in the request path. Do not include it in the request body.

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

`/scenarioConfigurations/{name}`

</td>
<td valign="top">

Create a new scenario configuration asynchronously \(returns 202\)

</td>
</tr>
</table>



## Create A Scenario Configuration with a Single Artifact

```
curl -X PUT "$AI_API_URL/v2/tcr/scenarioConfigurations/customer-churn-scenario" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
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
> Response — 202 Accepted:
> {
>   "name": "customer-churn-scenario"
> }
> 
> ```



## Create A Scenario Configuration with Multiple artifacts

A scenario can reference multiple Tabular Artifacts if the use case spans more than one table or file.

```
curl -X PUT "$AI_API_URL/v2/tcr/scenarioConfigurations/sales-forecast-scenario" \
  -H "Authorization: Bearer $TOKEN" \
  -H "AI-Resource-Group: $RESOURCE_GROUP" \
  -H "Content-Type: application/json" \
  -d '{
   "contextSelectionStrategy": "random",
    "tabularArtifacts": [
      { "name": "sales-data-ta" },
      { "name": "orders-parquet-ta" }
    ]
  }'

```

> ### Output Code:  
> ```
> Response — 202 Accepted:
> {
>   "name": "sales-forecast-scenario"
> }
> 
> ```



## Next Step

For more information about scenario configuration status, see [Retrieve a Scenario Configuartion](https://help.sap.com/docs/AI_CORE/b9f48eb4a993445b863a55dd4d38f64d/08068d97f8b845ffa3ff92586021ee0e.html?locale=en-US&state=DRAFT&version=CLOUD).

-   **[Manage Scenario Configurations](manage-scenario-configurations-08068d9.md)**  


