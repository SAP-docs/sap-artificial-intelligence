<!-- loio1fa895527bd64c6c878733e293da99dc -->

# Stop a Single Deployment

Stopping a deployment releases the SAP AI Core runtime computing resources that it used. A stopped deployment does not incur costs.

> ### Note:  
> Stop is only enabled if the status is running or pending.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_rst_3f2_5cc"/>

## Procedure

Update the deployment by submitting a PATCH request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

Update the request body to:

```
curl --request PATCH $AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID \
--header "authorization: Bearer $TOKEN" \
--header "AI-Resource-Group: $RESOURCE_GROUP" \
--header 'content-Type: application/json' \
--data-raw '{
"targetStatus": "STOPPED"
}'

```

> ### Output Code:  
> ```
> {
>     "id": "d748fdae9f88a9b0",
>     "message": "Deployment modification scheduled"
> }
> 
> ```



<a name="task_i3h_n13_tcc__postreq_btd_hxs_zxb"/>

## Next Steps

Check the status of the deployment by submitting a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

```
curl --request GET $AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID \ --header "Authorization: Bearer $TOKEN" \ --header "AI-Resource-Group: $RESOURCE_GROUP"
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_zk2_jh2_5cc"/>

## Procedure

Stop the deployment by submitting a PATCH request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`. The header for this request is: `AI-Resource-Group: {YOUR-Resource-Group}`. The `Body` for this request is:

```
{
"targetStatus": "STOPPED"
}
```



<a name="task_cxf_n13_tcc__postreq_ndq_yws_zxb"/>

## Next Steps

Check the status of the deployment by submitting a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

