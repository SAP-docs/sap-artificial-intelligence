<!-- loio26d119e19dc94accad3e06afa95c231e -->

# Delete a Custom Metric

You can delete a single metric using its ID by sending a DELETE request to the endpoint `$AI_API_URL/v2/lm/evaluationMetrics/$EVALUATION_METRIC_ID`.

> ### Caution:  
> Deletion cannot be reversed.

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


This endpoint returns a response code. Successful requests return code 204.

```
curl --request DELETE \
  --url {{AI_API_URL}}/v2/lm/evaluationMetrics/{{evaluationMetricId}} \  
  --header 'AI-Resource-Group: $RESOURCE_GROUP' \
  --header 'Authorization: Bearer $TOKEN'
```

Error responses include:

-   **403 Forbidden**: Insufficient permissions or invalid tenant authorization
-   **404 Not Found**: Metric with the specified UUID \(metric ID\) does not exist

