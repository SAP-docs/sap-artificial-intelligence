<!-- loio3f88c30813704fd9ba7be3a256afa3c6 -->

# Edit a Resource Group

> ### Note:  
> Resource group Ids must be of length minimum: 3, maximum: 253. The first and last characters must be either a lower case letter, an upper case letter or a number. Character entries from the second to penultimate, may include a lower case letter, an upper case letter, a number, a full stop or a hyphen. No other special characters are permitted.



<a name="loio3f88c30813704fd9ba7be3a256afa3c6__section_wbq_3wg_k5b"/>

## Using Postman

1.  Send a PATCH request to the endpoint `{{apiurl}}/v2/admin/resourceGroups/{{resource_group_name}}` with the body:

    ```json
    {
        "resourceGroupId": "<ID of your resource group>"
    }
    ```




<a name="loio3f88c30813704fd9ba7be3a256afa3c6__section_zbq_3wg_k5b"/>

## Using curl

1.  Create a resource group by sending the following:

    ```
    curl --location --request PATCH "$AI_API_URL/v2/admin/resourceGroups/{{resource_group_name}}" --header "Authorization: Bearer $TOKEN" --header 'Content-Type: application/json' --data-raw '{ "resourceGroupId": "<ID of your resource group>"}'
    
    ```


**Parent topic:**[Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group is a unique dedicated namespace or workspace environment, where users can create or add configurations, executions, deployments, and artifacts. They are used for running training jobs or model servers.")

**Related Information**  


[Create a Resource Group](create-a-resource-group-01753f4.md "")

[Delete a Resource Group](delete-a-resource-group-40d83a2.md "")

