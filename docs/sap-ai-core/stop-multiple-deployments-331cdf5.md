<!-- loio331cdf505d1c47618256a83920dd7c9a -->

# Stop Multiple Deployments



`bulkUpdates` is a meta capability endpoint of the AI API. It enables or disables bulk PATCH operations. For more information, see [About the AI API](about-the-ai-api-716d4c3.md).

The feature is set to false by default. To enable bulk PATCH operations, your template must contain the following snippet, with the relevant values set to `true`.

```

Meta:
  "bulkUpdates": {
        "executions": false,
        "deployments": false
      }
```

About `bulkUpdates`:

-   The maximum number of updates per request is 100.

-   Your bulk update can contain a mixture of STOP and DELETE requests.

-   Only *running* or *pending* executions or deployments can be stopped.

-   Only *stopped*, *dead* or *unknown* executions or deployments can be deleted.

-   An ID can only appear once per bulk request. For multiple modifications of the same ID, multiple requests are needed.




<a name="loio331cdf505d1c47618256a83920dd7c9a__section_sfh_r2m_jwb"/>

## Using curl

Update the request body to:

```
curl --request PATCH  - /deployments \
    --header {"deployments": [
    {
      "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
      "targetStatus": "STOPPED"
    },
    {
      "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
      "targetStatus": "DELETED"
    }
  ]
}

```

> ### Output Code:  
> ```
> {
>   "deployments": [
>     {
>       "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "message": "Deployment modification scheduled"
>     },
>     {
> 
>       "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
>       "message": "Deployment modification scheduled"
>     }
>   ]
> }
> 
> ```



<a name="loio331cdf505d1c47618256a83920dd7c9a__section_f51_13m_jwb"/>

## Using Postman

Send a bulk PATCH request to: `- /deployments`

```
{
"deployments": [
    {
      "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
      "targetStatus": "STOPPED"
    },
    {
      "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
      "targetStatus": "DELETED"
    }
  ]
}
}'

```

> ### Output Code:  
> ```
> {
>   "deployments": [
>     {
>       "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "message": "Deployment modification scheduled"
>     },
>     {
> 
>       "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
>       "message": "Deployment modification scheduled"
>     }
>   ]
> }
> 
> ```

**Parent topic:**[Stop Deployments](stop-deployments-b7d2577.md " ")

**Related Information**  


[Stop a Single Deployment](stop-a-single-deployment-1fa8955.md "")

[About the AI API](about-the-ai-api-716d4c3.md "The AI API lets you manage your AI assets (such as training scripts, data, models, and model servers) across multiple runtimes.")

