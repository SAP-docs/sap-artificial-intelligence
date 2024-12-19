<!-- loio40d83a2716894174b4b9b407396a0708 -->

# Delete a Resource Group

**Parent topic:**[Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group is a unique dedicated namespace or workspace environment, where users can create or add configurations, executions, deployments, and artifacts. They are used for running training jobs or model servers.")

**Related Information**  


[Create a Resource Group](create-a-resource-group-01753f4.md "")

[Edit a Resource Group](edit-a-resource-group-3f88c30.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_ajf_fcy_ycc"/>

## Procedure

Run the following code:

```
curl --location --request POST "$AI_API_URL/v2/admin/resourceGroups/{{resource_group_name}}" --header "Authorization: Bearer $TOKEN" --header 'Content-Type: application/json' --data-raw '{ "resourceGroupId": "<ID of your resource group>"}'

```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using Postman



<a name="task_cxf_n13_tcc__steps_vbp_xcy_ycc"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/admin/resourceGroups/{{resource_group_name}}`.

