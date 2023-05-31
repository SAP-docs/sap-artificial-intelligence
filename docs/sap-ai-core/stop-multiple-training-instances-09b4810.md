<!-- loio09b4810ad29445d19025836ed1ac5151 -->

# Stop Multiple Training Instances



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




<a name="loio09b4810ad29445d19025836ed1ac5151__section_tfh_r2m_jwb"/>

## Using Postman

Send a bulk PATCH request to the endpoint: `- /executions`

Update the request body to:

```
{
  "executions": [
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
>   "executions": [
>     {
>       "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "message": "Execution modification scheduled"
>     },
>     {
> 
>       "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
>       "message": "Execution modification scheduled"
>     }
>   ]
> }
> 
> ```



<a name="loio09b4810ad29445d19025836ed1ac5151__section_sfh_r2m_jwb"/>

## Using curl

Update the request body to:

```
curl --request PATCH  - /executions \
    --header {"executions": [
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
>   "executions": [
>     {
>       "id": "aa97b177-9383-4934-8543-0f91a7a0283a",
>       "message": "Execution modification scheduled"
>     },
>     {
> 
>       "id": "qweq32131-qwee-1231-8543-0f91a7a2e2e",
>       "message": "Execution modification scheduled"
>     }
>   ]
> }
> 
> ```

**Parent topic:** [Stop Training Instances](stop-training-instances-3d85344.md "")

**Related Information**  


[Stop a Single Training Instance](stop-a-single-training-instance-07870df.md "")

[About the AI API](about-the-ai-api-716d4c3.md "The AI API lets you manage your AI assets (such as training scripts, data, models, and model servers) across multiple runtimes.")

