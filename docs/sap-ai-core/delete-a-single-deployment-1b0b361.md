<!-- loio1b0b3612e5f948a6af5e593a61f711ce -->

# Delete a Single Deployment

Deleting a deployment releases the SAP AI Core resources that it used.

> ### Restriction:  
> If your deployment is running, you must stop it first.You can stop a deployment by submitting a PATCH request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`. For more information, see [Stop a Single Deployment](stop-a-single-deployment-1fa8955.md)

**Parent topic:**[Delete Deployments](delete-deployments-0193d17.md " ")

**Related Information**  


[Delete Multiple Deployments](delete-multiple-deployments-6b521aa.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_ulk_mnd_5cc"/>

## Procedure

1.  Update the deployment by submitting a DELETE request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

2.  Update the request body to:

    ```
    curl --request DELETE $AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID \
    --header "authorization: Bearer $TOKEN" \
    --header "ai-resource-group: $RESOURCE_GROUP" \
    --header 'content-Type: application/json' \
    --data-raw '{
    "targetStatus": "DELETED"
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

3.  Check the status of the deployment by submitting a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

    ```
    curl --request GET $AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID \ --header "Authorization: Bearer $TOKEN" \ --header "ai-resource-group: $RESOURCE_GROUP"
    ```


<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_fs5_dzd_cyb"/>

## Procedure

Delete the deployment by submitting a PATCH request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`. The header for this request is: `AI-Resource-Group: {YOUR-Resource-Group}`. The `Body` for this request is:

```
{
"targetStatus": "DELETED"
}
```



<a name="task_cxf_n13_tcc__postreq_ndq_yws_zxb"/>

## Next Steps

Check the status of the deployment by submitting a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.

