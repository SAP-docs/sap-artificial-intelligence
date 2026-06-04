<!-- loio40d83a2716894174b4b9b407396a0708 -->

# Delete a Resource Group

Deletes a resource group that is invalid, contains errors, or is no longer required.

**Parent topic:**[Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group is a unique dedicated namespace or workspace environment, where users can create or add configurations, executions, deployments, and artifacts. They are used for running training jobs or model servers.")

**Related Information**  


[Create a Resource Group](create-a-resource-group-01753f4.md "")

[Edit a Resource Group](edit-a-resource-group-3f88c30.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using the API



## Context

> ### Remember:  
> When you delete a resource group, [Manage mTLS Certificate Secrets](manage-mtls-certificate-secrets-200810f.md) in that group are deleted. Certificates that were issued before the deletion may remain valid until they expire. You are responsible for removing or revoking trust on any external services that rely on those certificates.



<a name="task_i3h_n13_tcc__steps_ajf_fcy_ycc"/>

## Procedure

Run the following code:

```
curl --location --request POST "$AI_API_URL/v2/admin/resourceGroups/{{resource_group_name}}"
--header "Authorization: Bearer $TOKEN"
--header 'Content-Type: application/json'
--data-raw '{
"resourceGroupId": "<ID of your resource group>"
}'

```



## Results

Successful responses return code **202** and include a success message.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



## Context

> ### Remember:  
> When you delete a resource group, [Manage mTLS Certificate Secrets](manage-mtls-certificate-secrets-200810f.md) in that group are deleted. Certificates that were issued before the deletion may remain valid until they expire. You are responsible for removing or revoking trust on any external services that rely on those certificates.



<a name="task_cxf_n13_tcc__steps_vbp_xcy_ycc"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/admin/resourceGroups/{{resource_group_name}}`.

