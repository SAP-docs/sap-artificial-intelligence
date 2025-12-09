<!-- loioab1160ebd60d4f4c86d1a723cca0c90c -->

# Create a Custom Metric



<a name="loioab1160ebd60d4f4c86d1a723cca0c90c__section_kp1_czg_lgc"/>

## Prerequisites

You have prepared your custom metric. For more information, see [Custom Metrics](custom-metrics-35dcc3e.md).



<a name="loioab1160ebd60d4f4c86d1a723cca0c90c__section_jwg_ssg_lgc"/>

## Procedure

Send a POST request to the endpoint `$AI_API_URL/v2/lm/evaluationMetrics`.

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

Include the following in your request body:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`scenario` 

</td>
<td valign="top">

The evaluation scenario ID and description this metric belongs to

</td>
</tr>
<tr>
<td valign="top">

`name` 

</td>
<td valign="top">

Metric identifier \(1-120 characters, no forward slashes\)

</td>
</tr>
<tr>
<td valign="top">

`version` 

</td>
<td valign="top">

Version string \(1-10 characters\)

</td>
</tr>
<tr>
<td valign="top">

`evaluationMethod` 

</td>
<td valign="top">

"llm-as-a-judge"

</td>
</tr>
<tr>
<td valign="top">

`spec` 

</td>
<td valign="top">

Your custom metric specification. For more information, see [Custom Metrics](custom-metrics-35dcc3e.md).

</td>
</tr>
<tr>
<td valign="top">

`description`\(optional\)

</td>
<td valign="top">

Your choice of description of the metric \(up to 512 characters\)

</td>
</tr>
<tr>
<td valign="top">

`metricType` \(optional\)

</td>
<td valign="top">

Purpose of the metric. Choose from: `agentic`, `optimization`, or `evaluation`.

</td>
</tr>
<tr>
<td valign="top">

`includeProperties` \(optional\)

</td>
<td valign="top">

An array of context properties to include.

Choose from: `prompt`, `grounding_query`, `grounding_response` or `reference`.

</td>
</tr>
</table>

> ### Restriction:  
> The maximum size of the payload of a custom metric object is 512 KB.
> 
> For tenants, the total number of custom metric objects including revisions is 50.

```

curl --request POST \
  --url $AI_API_URL/v2/lm/evaluationMetrics \
  --header 'AI-Resource-Group: $RESOURCE_GROUP' \
  --header 'Content-Type: application/json' \ 
  --header 'Authorization: Bearer $TOKEN'
  --data '{
	  "scenario": "qa-evaluation",
	  "name": "factual-accuracy",
	  "version": "1.0",
	  "description": "Measures factual correctness of responses",
	  "evaluationMethod": "llm-as-a-judge",
	  "metricType": "evaluation",
	  "includeProperties": ["prompt", "reference"],
	  "spec": ...  // Custom Metric Definition
}'

```



<a name="loioab1160ebd60d4f4c86d1a723cca0c90c__section_i2y_g1h_lgc"/>

## Results

Your response will include one of the following response codes:

-   **Successful** response codes:
    -   **201**

-   **Error** response codes:
    -   **400 Bad Request**: Invalid request format, missing required fields, or validation errors
    -   **403 Forbidden**: Insufficient permissions or invalid tenant authorization
    -   **409 Conflict**: A metric with the same scenario, name, and version already exists


Successful responses will include a unique ID that can be used to retrieve your custom metric later.

> ### Output Code:  
> ```
> {
> "message": "<success message>"
> "id": "<metric ID>" 
> "scenario": "<scenario ID>"
> "name": "<name>"
> "version": "<version>"
> }
> ```

