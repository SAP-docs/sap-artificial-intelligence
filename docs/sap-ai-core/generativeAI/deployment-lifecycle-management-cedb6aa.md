<!-- copycedb6aa1f4e343579809b5e9729cacf9 -->

# Deployment Lifecycle Management



## Context

> ### Restriction:  
> Only deployments in a stopped state can be deleted.

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
</table>



<a name="copycedb6aa1f4e343579809b5e9729cacf9__concept_xmv_3hb_3zb"/>

## Stop a Deployment

Send a PATCH request to the endpoint `$AI_API_URL/v2/lm/deployments/<deploymentid>`. Include the ID of the deployment that you want to stop in your request:

> ### Sample Code:  
> ```
> curl PATCH '$AI_API_URL/v2/lm/deployments/<deploymentid>' \
> --header 'AI-Resource-Group: default' \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
> "targetStatus": "STOPPED"
> }'
> ```



<a name="copycedb6aa1f4e343579809b5e9729cacf9__concept_uqf_lhb_3zb"/>

## Delete a Deployment

Send a DELETE request to the endpoint `$AI_API_URL/v2/lm/deployments/<deploymentid>`. Include the ID of the deployment that you want to stop in your request.

> ### Sample Code:  
> ```
> curl DELETE '$AI_API_URL/v2/lm/deployments/<deploymentid>' \
> --header 'AI-Resource-Group: default' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> 
> ```

