<!-- loioc1c3cc3e3f88417ba785ab8e29564e82 -->

# Delete Multiple Training Instances



`bulkUpdates` is a meta capability endpoint of the AI API. It enables or disables bulk PATCH operations. For more information, see [AI API Overview](ai-api-overview-716d4c3.md).

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




<a name="loioc1c3cc3e3f88417ba785ab8e29564e82__section_sfh_r2m_jwb"/>

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



<a name="loioc1c3cc3e3f88417ba785ab8e29564e82__section_tfh_r2m_jwb"/>

## Using Postman

Send a bulk PATCH request to: `- /executions`

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
> 
> ```

**Parent topic:**[Delete Training Instances](delete-training-instances-612ce17.md "")

**Related Information**  


[Delete a Single Training Instance](delete-a-single-training-instance-dd71f16.md "")

[AI API Overview](ai-api-overview-716d4c3.md "The AI API lets you manage your AI assets (such as training scripts, data, models, and model servers) across multiple runtimes.")

