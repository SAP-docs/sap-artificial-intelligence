<!-- loio6b521aa3dfa1465a9be658bdb38fb2e5 -->

# Delete Multiple Deployments

Deleting a deployment releases the SAP AI Core resources that it used.

> ### Restriction:  
> If your deployment is running, you must stop it first.You can stop a deployment by submitting a PATCH request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`. For more information, see [Stop Multiple Deployments](stop-multiple-deployments-331cdf5.md).



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


**Parent topic:**[Delete Deployments](delete-deployments-0193d17.md " ")

**Related Information**  


[Delete a Single Deployment](delete-a-single-deployment-1b0b361.md "")

[AI API Overview](ai-api-overview-716d4c3.md "The AI API lets you manage your AI assets (such as training scripts, data, models, and model servers) across multiple runtimes.")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_lx2_x2z_zxb"/>

## Procedure

Send a bulk PATCH request to the endpoint: `- /deployments`

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

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using Postman



<a name="task_cxf_n13_tcc__steps_lx2_x2z_zxb1"/>

## Procedure

Send a bulk PATCH request to the endpoint: `- /deployments`

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

