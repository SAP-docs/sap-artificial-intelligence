<!-- loio40d83a2716894174b4b9b407396a0708 -->

# Delete a Resource Group



<a name="loio40d83a2716894174b4b9b407396a0708__section_wbq_3wg_k5b"/>

## Using Postman

Send a DELETE request to the endpoint `{{apiurl}}/v2/admin/resourceGroups/{{resource_group_name}}`.



<a name="loio40d83a2716894174b4b9b407396a0708__section_zbq_3wg_k5b"/>

## Using curl

1.  Create a resource group by sending the following:

    ```
    curl --location --request POST "$AI_API_URL/v2/admin/resourceGroups/{{resource_group_name}}" --header "Authorization: Bearer $TOKEN" --header 'Content-Type: application/json' --data-raw '{ "resourceGroupId": "<ID of your resource group>"}'
    
    ```


**Parent topic:**[Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group is a unique dedicated namespace or workspace environment, where users can create or add configurations, executions, deployments, and artifacts. They are used for running training jobs or model servers.")

**Related Information**  


[Create a Resource Group](create-a-resource-group-01753f4.md "")

[Edit a Resource Group](edit-a-resource-group-3f88c30.md "")

