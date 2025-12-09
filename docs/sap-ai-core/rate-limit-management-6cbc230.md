<!-- loio6cbc230d86874672b03c1eb0ac89b092 -->

# Rate Limit Management

Quota-management APIs let you check and modify rate-limits for generative AI model inference calls.

AI Core implements rate-limiting controls that restrict the number of requests per minute \(RPM\) for each model within a tenant environment. When these limits are exceeded, the system responds with a 429 error code.

The rate-limits are model-specific and reset on a per-minute basis.

By default, all resource groups within a tenant operate under the same rate-limit threshold, though this can be customized through specific configuration. Additionally, all versions of a particular model share the same configured rate-limit allocation.

You can use the following API endpoints to check your quota limits and request quota limit updates.

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

Bearer $AUTH\_TOKEN

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



## Get Rate Limits

Send a GET request to the endpoint `$AI_API_URL/v2/admin/quota/model`,

For example:

```

curl --location "$AI_API_URL/v2/admin/quota/model" \
--header "Authorization: Bearer $AUTH_TOKEN"
```

> ### Output Code:  
> ```
> [
>   {
>     "resourceType": "model",
>     "quotaDetails": [
>       {
>         "unit": "requestPerMinute",
>         "limit": 78,
>         "descriptors": {
>            "modelName": "gpt-5",
>            "modelVersion": "*",
>            "providerName": "azure-openai"
>         }
>       },
>       //... other models
>     ]
>   }
> ]
> ```

By default, tenant-level quota applies to all resource groups. If quota is requested for a specific resource-group, it'll appear as part of the response. To get a resource group level quota, include a resource group in your request. For example:

```

curl --location "$AI_API_URL/v2/admin/quota/model" \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header "Authorization: Bearer $AUTH_TOKEN"
```



## Create a Rate Limit Update

You can request a rate limit update by sending a POST request to the endpoint `$AI_API_URL/v2/admin/quota/requests`. Include the details of your rate limit update in your request.



### Tenant level Request

Populate the following request with your values:

```
curl --location "$AI_API_URL/v2/admin/quota/requests" \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
  "resourceType": "model",
  "quotaDetails": {
    "unit": "requestPerMinute",
    "limit": <new limit>,
    "descriptors": {
      "modelName": "<modelName>",
      "providerName": "<model provider executableId>"
    }
  },
  "reason": "<Provide a reason for quota update request>"
}'
 
```

> ### Output Code:  
> ```
> {
> "requestId": "5ed1d56f-3d0c-45a4-aa55-1b97020fa714",
> "message": "The request has been submitted for approval."
> } 
> ```



### Resource Group Level requests

To request a rate limit update for a particular resource-group, include the resource group in your header and include `scope: resource_group` in your request.

For example:

```
curl --location "$AI_API_URL/v2/admin/quota/requests" \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
  "resourceType": "model",
  "scope": "resource_group",
  "quotaDetails": {
    "unit": "requestPerMinute",
    "limit": <new limit>,
    "descriptors": {
      "modelName": "<modelName>",
      "providerName": "<model provider executableId>"
    }
  },
  "reason": "<Provide a reason for quota update request>"
}'
 
```



## List Rate Limit Update Results

You can check the status of your rate limits by sending a GET request to the endpoint `$AI_API_URL/v2/admin/quota/requests`.

For example:

```
curl --location "$AI_API_URL/v2/admin/quota/requests" \
--header "Authorization: Bearer $AUTH_TOKEN"
```

For resource group level requests, include your resource group in the header. For example:

```
curl --location "$AI_API_URL/v2/admin/quota/requests" \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header "Authorization: Bearer $AUTH_TOKEN"
```

To follow up on a request create a SNOW support ticket for component CA-ML-AIC. For more information, see [Support Process](support-process-c484783.md) .

