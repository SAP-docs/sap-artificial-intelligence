<!-- loio2577090ae91a420f8a52c5f875de010e -->

# Prediction Examples for Tabular AI Orchestration

The following examples show common prediction scenarios supported by the Tabular AI Orchestration service.


<table>
<tr>
<th valign="top">

Example

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Prediction with context selection

</td>
<td valign="top">

Retrieves context rows from a registered tabular artifact before running predictions.

</td>
</tr>
<tr>
<td valign="top">

Prediction with context selection and user-provided context

</td>
<td valign="top">

Combines user-provided context rows with context rows selected by the service.

</td>
</tr>
<tr>
<td valign="top">

Multi-target prediction

</td>
<td valign="top">

Predicts multiple target columns in a single request.

</td>
</tr>
<tr>
<td valign="top">

Classification with top-K predictions

</td>
<td valign="top">

Returns multiple ranked prediction candidates for classification tasks.

</td>
</tr>
</table>



## Example 1: Prediction with Context Selection

```
curl -X POST "$DEPLOYMENT_URL/v1/predict" \
  -H "Content-Type: application/json" \
  -H "ai-main-tenant: <your-tenant-uuid>" \
  -H "ai-resource-group: <your-resource-group>" \
  -d '{
    "modelName": "sap-rpt-1-small",
    "scenarioConfigName": "my_scenario_config_name",
    "contextSelectionConfig": {
      "numRows": 200,
      "strategy": "random"
    },
    "predictionConfig": {
      "indexColumn": "requisition_id",
      "targetColumns": [
        {
          "name": "jobcode",
          "predictionPlaceholder": "[PREDICT]",
          "taskType": "classification"
        }
      ]
    },
    "columns": {
      "requisition_id": ["2927", "3144", "2403"],
      "country_id": ["US", "US", "US"],
      "hiring_manager_id": ["73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3"],
      "recruiter_id": ["131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F"],
      "jobcode": ["[PREDICT]", "[PREDICT]", "[PREDICT]"]
    }
  }'
```

> ### Output Code:  
> ```
> {
>   "id": "b782effe-6f2b-46ea-84cf-6c28790cf835",
>   "metadata": {
>     "num_columns": 5,
>     "num_rows": 203,
>     "num_predictions": 3,
>     "num_query_rows": 3
>   },
>   "predictions": [
>     {
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 2927
>     },
>     {
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 3144
>     },
>     {
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 2403
>     }
>   ],
>   "status": {
>     "code": 0,
>     "message": "ok"
>   }
> }
> ```



## Example 2: Predictions with context selection and user-provided context

```
curl -X POST "$DEPLOYMENT_URL/v1/predict" \
  -H "Content-Type: application/json" \
  -H "ai-main-tenant: <your-tenant-uuid>" \
  -H "ai-resource-group: <your-resource-group>" \
  -d '{
    "modelName": "sap-rpt-1-small",
    "scenarioConfigName": "my_scenario_config_name",
    "contextSelectionConfig": {
      "numRows": 200,
      "strategy": "random"
    },
    "predictionConfig": {
      "indexColumn": "requisition_id",
      "targetColumns": [
        {
          "name": "jobcode",
          "predictionPlaceholder": "[PREDICT]",
          "taskType": "classification"
        }
      ]
    },
    "columns": {
      "requisition_id": ["2927", "3144", "2403"],
      "country_id": ["US", "US", "US"],
      "hiring_manager_id": ["73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3"],
      "recruiter_id": ["131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F"],
      "jobcode": ["[PREDICT]", "[PREDICT]", "[PREDICT]"]
    },
    "contextColumns": {
      "requisition_id": ["29271", "31441", "24031"],
      "country_id": ["US", "US", "US"],
      "hiring_manager_id": ["73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3"],
      "recruiter_id": ["131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F"],
      "jobcode": ["ABcd", "ABcd", "ABcd"]
    }
  }'
```

> ### Output Code:  
> ```
> {
>   "id": "3768f648-1f4e-443b-832d-e474eefa1ec4",
>   "metadata": {
>     "num_columns": 5,
>     "num_rows": 206,
>     "num_predictions": 3,
>     "num_query_rows": 3
>   },
>   "predictions": [
>     {
>       "jobcode": [
>         {
>           "confidence": 0.5,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 2927
>     },
>     {
>       "jobcode": [
>         {
>           "confidence": 0.5,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 3144
>     },
>     {
>       "jobcode": [
>         {
>           "confidence": 0.5,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 2403
>     }
>   ],
>   "status": {
>     "code": 0,
>     "message": "ok"
>   }
> }
> ```



## Example 3: Multi-target Prediction with context selection

```
curl -X POST "$DEPLOYMENT_URL/v1/predict" \
  -H "Content-Type: application/json" \
  -H "ai-main-tenant: <your-tenant-uuid>" \
  -H "ai-resource-group: <your-resource-group>" \
  -d '{
    "modelName": "sap-rpt-1-small",
    "scenarioConfigName": "my_scenario_config_name",
    "contextSelectionConfig": {
      "numRows": 200,
      "strategy": "random"
    },
    "predictionConfig": {
      "indexColumn": "requisition_id",
      "targetColumns": [
        {
          "name": "jobcode",
          "predictionPlaceholder": "[PREDICT]",
          "taskType": "classification"
        },
        {
          "name": "country_id",
          "predictionPlaceholder": "[PREDICT]",
          "taskType": "classification"
        }
      ]
    },
    "columns": {
      "requisition_id": ["2927", "3144", "2403"],
      "country_id": ["[PREDICT]", "[PREDICT]", "[PREDICT]"],
      "hiring_manager_id": ["73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3"],
      "recruiter_id": ["131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F"],
      "jobcode": ["[PREDICT]", "[PREDICT]", "[PREDICT]"]
    }
  }'
```

> ### Output Code:  
> ```
> {
>   "id": "98492b16-c21d-4233-a701-56897226f884",
>   "metadata": {
>     "num_columns": 5,
>     "num_rows": 203,
>     "num_predictions": 6,
>     "num_query_rows": 3
>   },
>   "predictions": [
>     {
>       "country_id": [
>         {
>           "confidence": 1.0,
>           "confidence_interval": null,
>           "prediction": "US"
>         }
>       ],
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 2927
>     },
>     {
>       "country_id": [
>         {
>           "confidence": 1.0,
>           "confidence_interval": null,
>           "prediction": "US"
>         }
>       ],
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 3144
>     },
>     {
>       "country_id": [
>         {
>           "confidence": 1.0,
>           "confidence_interval": null,
>           "prediction": "US"
>         }
>       ],
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         }
>       ],
>       "requisition_id": 2403
>     }
>   ],
>   "status": {
>     "code": 0,
>     "message": "ok"
>   }
> }
> ```



## Example 4: Classification with Top-K Predictions

```
curl -X POST "$DEPLOYMENT_URL/v1/predict" \
  -H "Content-Type: application/json" \
  -H "ai-main-tenant: <your-tenant-uuid>" \
  -H "ai-resource-group: <your-resource-group>" \
  -d '{
    "modelName": "sap-rpt-1-large",
    "scenarioConfigName": "my_scenario_config_name",
    "contextSelectionConfig": {
      "numRows": 200,
      "strategy": "random"
    },
    "predictionConfig": {
      "indexColumn": "requisition_id",
      "targetColumns": [
        {
          "name": "jobcode",
          "predictionPlaceholder": "[PREDICT]",
          "taskType": "classification",
          "topK": 4
        },
        {
          "name": "country_id",
          "predictionPlaceholder": "[PREDICT]",
          "taskType": "classification",
          "topK": 2
        }
      ]
    },
    "columns": {
      "requisition_id": ["2927", "3144", "2403"],
      "country_id": ["US", "IN", "[PREDICT]"],
      "hiring_manager_id": ["73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3", "73F840E39C51453EBCF034735E6A28F3"],
      "recruiter_id": ["131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F", "131A0E2C84E54433B25560D7087D064F"],
      "jobcode": ["[PREDICT]", "[PREDICT]", "[PREDICT]"]
    }
  }'
```

> ### Output Code:  
> ```
> {
>   "id": "d840df26-2fc5-4823-9295-78ed614cf1bd",
>   "metadata": {
>     "num_columns": 5,
>     "num_rows": 203,
>     "num_predictions": 6,
>     "num_query_rows": 3
>   },
>   "predictions": [
>     {
>       "country_id": [
>         {
>           "confidence": 1.0,
>           "confidence_interval": null,
>           "prediction": "US"
>         },
>         {
>           "confidence": 0.0,
>           "confidence_interval": null,
>           "prediction": "IN"
>         }
>       ],
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         },
>         {
>           "confidence": 0.45,
>           "confidence_interval": null,
>           "prediction": "Atech"
>         },
>         {
>           "confidence": 0.01,
>           "confidence_interval": null,
>           "prediction": "ADMIN"
>         },
>         {
>           "confidence": 0.01,
>           "confidence_interval": null,
>           "prediction": "00001"
>         }
>       ],
>       "requisition_id": 2927
>     },
>     {
>       "country_id": [
>         {
>           "confidence": 1.0,
>           "confidence_interval": null,
>           "prediction": "US"
>         },
>         {
>           "confidence": 0.0,
>           "confidence_interval": null,
>           "prediction": "IN"
>         }
>       ],
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         },
>         {
>           "confidence": 0.45,
>           "confidence_interval": null,
>           "prediction": "Atech"
>         },
>         {
>           "confidence": 0.01,
>           "confidence_interval": null,
>           "prediction": "ADMIN"
>         },
>         {
>           "confidence": 0.01,
>           "confidence_interval": null,
>           "prediction": "00001"
>         }
>       ],
>       "requisition_id": 3144
>     },
>     {
>       "country_id": [
>         {
>           "confidence": 1.0,
>           "confidence_interval": null,
>           "prediction": "US"
>         },
>         {
>           "confidence": 0.0,
>           "confidence_interval": null,
>           "prediction": "IN"
>         }
>       ],
>       "jobcode": [
>         {
>           "confidence": 0.53,
>           "confidence_interval": null,
>           "prediction": "AEng"
>         },
>         {
>           "confidence": 0.45,
>           "confidence_interval": null,
>           "prediction": "Atech"
>         },
>         {
>           "confidence": 0.01,
>           "confidence_interval": null,
>           "prediction": "ADMIN"
>         },
>         {
>           "confidence": 0.01,
>           "confidence_interval": null,
>           "prediction": "00001"
>         }
>       ],
>       "requisition_id": 2403
>     }
>   ],
>   "status": {
>     "code": 0,
>     "message": "ok"
>   }
> }
> ```

> ### Note:  
> The response returns `203` rows in `num_rows`, including 200 rows from the orchestrated context selection configured in `contextSelectionConfig.numRows` and 3 query rows provided in the request.

