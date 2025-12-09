<!-- loio009c72411ac148369aad2e11203dfcd1 -->

# Retrieve Custom Metrics

You can use the following endpoints to view your custom metrics and their details:



<a name="loio009c72411ac148369aad2e11203dfcd1__section_v3p_3th_lgc"/>

## Listing Custom Metrics

You can retrieve a list of your custom metrics by sending a GET request to the endpoint `$AI_API_URL/v2/lm/evaluationMetrics`.

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
</table>

```
curl --request GET \
  --url $AI_API_URL/v2/lm/evaluationMetrics \  
  --header 'AI-Resource-Group: {{resource_group}}' \
  --header 'Authorization: Bearer {{access_token}}' 

```

This endpoint returns a response in JSON format containing details of your custom metrics.

You can add filters to your list by including the following parameters:

-   `scenario`: Filter metrics by scenario ID
-   `name`: Filter metrics by metric name \(for example, "groundedness"\)
-   `version`: Filter metrics by specific version
-   `evaluationMethod`: Filter by evaluator type \(for example., "llm-as-a-judge"\)
-   `retrieve`: What type of metrics to retrieve - "imperative", "declarative", or "both" \(default: "both"\)
-   `includeSpec`: Whether to include the full metric specification in response \(default: false\)
-   `includeSystemMetrics`: Whether to include system-defined metrics \(default: true\)

For example:

```
curl --request GET \  
  ---url $AI_API_URL/v2/lm/evaluationMetrics \
  --header 'AI-Resource-Group: $RESOURCE_GROUP' \
  --header 'Content-Type: application/json' \ 
  --header 'Authorization: Bearer $TOKEN'
  --data '{
	"params" = {
		"scenario": "genai-evaluations",
		"includeSpec": "true"
		"name": "factual-accuracy",
		"evaluationMethod": "llm-as-a-judge"
	}
}'
```

Error responses include:

-   **400 Bad Request**: Invalid query parameters or request format
-   **403 Forbidden**: Insufficient permissions or invalid tenant authorization

Succesful responses include the following:

> ### Output Code:  
> ```
> {
> "count": ... ,  // Number of items retrieved
> "resources": ... , // List of MetricItem
> }
> ```



<a name="loio009c72411ac148369aad2e11203dfcd1__section_e1m_jth_lgc"/>

## Get a Metric by ID

You can retrieve the details of a single metric using its ID by sending a GET request to the endpoint `$AI_API_URL/v2/lm/evaluationMetrics/$EVALUATION_METRIC_ID`.

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
</table>

Populate the code snippet with the following:

-   Your metric ID


```
curl --request GET \
  --url $AI_API_URL/v2/lm/evaluationMetrics/$EVALUATION_METRIC_ID \  
  --header 'AI-Resource-Group: $RESOURCE_GROUP' \
  --header 'Authorization: Bearer $TOKEN' 

```

This endpoint returns a response in JSON format containing details of your custom metric.

Error responses include:

-   **400 Bad Request**: Invalid UUID \(metric ID\) format
-   **403 Forbidden**: Insufficient permissions or invalid tenant authorization
-   **404 Not Found**: Metric with the specified UUID \(metric ID\) does not exist

Metrics are returned in the following format:

> ### Output Code:  
> ```
> 
> {"scenario": ... ,     
> "name": ... ,             
> "version": ... ,          
> "evaluationMethod": ... , 
> "id": ... ,               
> "spec": ... ,        
> "description": ... ,
> "metricType": ... ,
> "includeProperties": ... ,    
> "managedBy": ... ,
> "createdAt": ... ,
> "additionalProperties": ...
> }
> ```



<a name="loio009c72411ac148369aad2e11203dfcd1__section_drk_sth_lgc"/>

## Get Metric History

You can retrieve the history of a single metric by sending a GET request to the endpoint `$AI_API_URL/v2/lm/scenarios/$SCENARIO/evaluationMetrics/$NAME/versions/$VERSION/history.`.

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
</table>

Populate the code snippet with the following:

-   `scenario`: The scenario the metric belongs to

-   `name`: The metric name

-   `version`: The specific version of the metric


```
curl --request GET \
--url $AI_API_URL/v2/lm/scenarios/$SCENARIO/evaluationMetrics/$NAME/versions/$VERSION/history. \  
  --header 'AI-Resource-Group: $RESOURCE_GROUP' \
  --header 'Authorization: Bearer $TOKEN'
```

This endpoint returns a response in JSON format containing a count and an array of custom metrics of the specified scenario, name, and version, sorted from newest to oldest.

Error responses include:

-   **400 Bad Request**: Invalid path parameters or request format
-   **403 Forbidden**: Insufficient permissions or invalid tenant authorization
-   **404 Not Found**: Metric with the specified scenario/name/version does not exist

> ### Output Code:  
> ```
> 
> {
> "count": ... ,  // Number of items retrieved
> "resources": ... , // List of MetricItem
> }
> ```

