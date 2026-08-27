<!-- loio6cbc230d86874672b03c1eb0ac89b092 -->

# Rate Limit Management

Quota-management APIs let you check and modify rate limits for generative AI model inference calls.

SAP AI Core implements rate-limiting controls that restrict the number of Requests Per Minute \(RPM\) for each model within a tenant environment. When these limits are exceeded, the system responds with a 429 error code.

The rate limits are model-specific and reset on a per-minute basis.

By default, all resource groups within a tenant operate under the same rate-limit threshold, although you can customize this behavior through specific configuration. Additionally, all versions of a particular model share the same configured rate-limit allocation.

For a tenant containing resource group \(RG\) 1 and resource group 2: if RG1 has a rate limit of 12k, and RG2 has a rate limit of 6k, the rate limit for the tenant must be at least 12k.



## 429 Too Many Requests

If an API returns HTTP status `429`, the request is rejected because the system cannot process it due to load or quota constraints. This response can indicate rate limits or temporary backend capacity issues.

**Common Causes and Mitigation**


<table>
<tr>
<th valign="top">

**Cause**

</th>
<th valign="top">

**Scope**

</th>
<th valign="top">

**Mitigation**

</th>
</tr>
<tr>
<td valign="top">

Tenant rate limit exceeded

</td>
<td valign="top">

All resource groups in tenant

</td>
<td valign="top">

Retry with backoff, distribute load, request quota increase

</td>
</tr>
<tr>
<td valign="top">

Resource group rate limit exceeded

</td>
<td valign="top">

Specific resource group

</td>
<td valign="top">

Retry with backoff, isolate workloads, request quota increase

</td>
</tr>
<tr>
<td valign="top">

Hyperscaler capacity exceeded

</td>
<td valign="top">

Infrastructure level

</td>
<td valign="top">

Retry later using `Retry-After`

</td>
</tr>
</table>

> ### Note:  
> A `429` response does not always mean a rate limit is exceeded. It can also indicate temporary back-end saturation.



## Causes



### Tenant-Level Rate Limits

SAP AI Core enforces per-tenant rate limits measured in RPM.

All resource groups share this limit by default. When the combined request rate exceeds the threshold, subsequent requests return `429` until the next minute window.

-   Limits are model-specific
-   All model versions share the same limit
-   Limits reset every minute



### Resource Group-Level Rate Limits

You can configure rate limits for individual resource groups.

If configured, requests from that resource group use its dedicated limit instead of the shared tenant quota.



### Hyperscaler and Service Provider Limits

SAP AI Core forwards requests to underlying infrastructure such as Azure OpenAI and SAP services.

These services may reject requests when their capacity limits are reached, independent of SAP AI Core quotas.



## Response Headers

**Rate Limit Response Headers**


<table>
<tr>
<th valign="top">

**Header**

</th>
<th valign="top">

**Description**

</th>
</tr>
<tr>
<td valign="top">

`Retry-After`

</td>
<td valign="top">

Time in seconds to wait before retrying

</td>
</tr>
</table>



## Mitigation Strategies

> ### Note:  
> A `429` response indicates a temporary condition, not a system failure.



### Implement Retry Logic with Exponential Backoff

Use AI Core–enabled SDKs [Libraries and SDKs](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/499309d6e371419fb7a88b7d68c20a31.html "Explore additional SDKs and libraries that you can use with SAP AI Core.") :arrow_upper_right: to handle retry logic. The SDKs provide configurable retry behavior. Use them instead of calling the APIs directly.

If you do not use the SDKs, implement retry logic as follows:

> ### Note:  
> Do not retry immediately after a `429` response. Use exponential backoff with jitter to prevent thundering-herd behavior.

1.  When you receive a `429` response, wait for an initial interval \(for example, 1 second\).
2.  If the response includes a `Retry-After` header, use its value as the wait interval.
3.  After each failed retry, increase the wait time exponentially and add a small random jitter.
4.  Limit retries by using a maximum cap \(for example, 5 retries or 60 seconds total wait time\).



### Spread Requests Over Time

Avoid sending large request bursts. Distribute requests evenly to stay within limits.



### Cache Responses

Reuse responses for repeated prompts to reduce API calls.



### Use Model Fallbacks

Route requests to alternative models if the primary model is rate-limited.



### Isolate Workloads

Assign different applications to separate resource groups to prevent shared quota exhaustion.



## Request a Rate Limit Increase

Request a quota increase if mitigation strategies do not meet your workload requirements.

You can use the following API endpoints to check your quota limits and request updates to them.

Ensure that you've the following headers set:


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

The base URL of your SAP AI Core environment. This URL can also be set as an environment variable.

</td>
</tr>
</table>



## Check Current Limits

Send a GET request to the endpoint `$AI_API_URL/v2/admin/quota/model`

By default, you receive a **tenant-level** rate limit, and the quota applies to all resource groups.

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

If a quota is requested for a specific resource group, it appears as part of the response. For **resource-group-level** limits, include the `AI-Resource-Group` header.

For example:

```

curl --location "$AI_API_URL/v2/admin/quota/model" \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header "Authorization: Bearer $AUTH_TOKEN"
```



## Submit a Request

You can request a rate limit update by sending a POST request to the endpoint `$AI_API_URL/v2/admin/quota/requests`. Include the details of your rate limit update in your request.

> ### Note:  
> A successful submission of a rate-limit increase request returns a `requestId`. Requests go through an approval process.



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

> ### Note:  
> A successful submission of a rate-limit increase request returns a `requestId`. Requests go through an approval process.

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



## Check Request Status

You can check the status of your rate limits by sending a GET request to the endpoint `$AI_API_URL/v2/admin/quota/requests`.

For example:

```
curl --location "$AI_API_URL/v2/admin/quota/requests" \
--header "Authorization: Bearer $AUTH_TOKEN"
```

For resource group scope, add `"scope": "resource_group"` and include the `AI-Resource-Group` header.

```
curl --location "$AI_API_URL/v2/admin/quota/requests" \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header "Authorization: Bearer $AUTH_TOKEN"
```

To follow up on a request, create a support ticket on component CA-ML-AIC. For more information, see [Support Process](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c484783c76c142bbaacb2ecbf9100661.html "Explore solutions to potential issues, and find out how to get support.") :arrow_upper_right: .

