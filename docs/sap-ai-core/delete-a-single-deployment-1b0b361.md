<!-- loio1b0b3612e5f948a6af5e593a61f711ce -->

# Delete a Single Deployment



<a name="loio1b0b3612e5f948a6af5e593a61f711ce__section_f2y_vbd_25b"/>

## Using Postman

Delete the deployment by submitting a DELETE request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`. The header for this request is: `AI-Resource-Group: {YOUR-Resource-Group}`.

Check the status of the deployment by submitting a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`.



<a name="loio1b0b3612e5f948a6af5e593a61f711ce__section_dnd_s3d_25b"/>

## Using curl

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


**Parent topic:**[Delete Deployments](delete-deployments-0193d17.md " ")

**Related Information**  


[Delete Multiple Deployments](delete-multiple-deployments-6b521aa.md "")

