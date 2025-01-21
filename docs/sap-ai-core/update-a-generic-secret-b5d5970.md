<!-- loiob5d597051e494b49a4907470f1b238af -->

# Update a Generic Secret

To update a generic secret, use the PATCH endpoint as shown below. The PATCH operation replaces the secret with the data provided. This can be used for rotating secret credentials.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__context_l4b_qcf_zcc"/>

## Context

Generic Secrets are used in addition to store sensitive information when system secrets are not applicable, for example in integration use cases where SAP AI Core is an orchestration layer.

SAP AI Core lets you optionally use generic secrets at the following levels:

-   Main-tenant scope

-   Tenant wide level

-   Resource-group level


Generic secrets are different to system secrets \(such as object store, Docker registry, and so on\) and can be used to store sensitive information, either for the main tenant, for all of its resource groups, or for each resource group via an API. The latter can be attached to containers in executions or deployments as environment variables or volume mounts.

> ### Note: 
> In order to allow rotation of Tenant-Wide secrets for long-running deployments without restarting the deployment, the following guidelines must be followed:
> - The deployment MUST mount the Tenant-Wide secret. For more information see [Consume a Generic Secret as a Volume Mount](consume-generic-secrets-in-executions-or-deployments-185a324.md)
> - The deployment MUST monitor the mounted secret for changes instead of relying on an in-memory copy of the secret read from the mount.
> - When a Tenant-Wide secret is updated, the tenant is responsible for observing the response of /secrets/{secret-name} endpoint to ensure that the Replicator has successfully updated the secret in all resource groups.



<a name="task_i3h_n13_tcc__steps_m4b_qcf_zcc"/>

## Procedure

Submit a PATCH request to the endpoint `/v2/admin/secrets/"$SECRET_NAME"`. Specify the scope via the headers:

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
-   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

```
curl --location --request PATCH "$AI_API_URL/v2/admin/secrets/$SECRET_NAME" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--header 'AI-Resource-Group: default' \
--data-raw '{
		"data": {
			"some-credential": "bXktc2Vuc2l0aXZlLWRhdGE="
			}
}'
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using Postman



<a name="task_cxf_n13_tcc__context_n4t_ncf_zcc"/>

## Context

Generic Secrets are used in addition to store sensitive information when system secrets are not applicable, for example in integration use cases where SAP AI Core is an orchestration layer.

SAP AI Core lets you optionally use generic secrets at the following levels:

-   Main-tenant scope

-   Tenant wide level

-   Resource-group level


Generic secrets are different to system secrets \(such as object store, Docker registry, and so on\) and can be used to store sensitive information, either for the main tenant, for all of its resource groups, or for each resource group via an API. The latter can be attached to containers in executions or deployments as environment variables or volume mounts.

> ### Note: 
> In order to allow rotation of Tenant-Wide secrets for long-running deployments without restarting the deployment, the following guidelines must be followed:
> - The deployment MUST mount the Tenant-Wide secret. For more information see [Consume a Generic Secret as a Volume Mount](consume-generic-secrets-in-executions-or-deployments-185a324.md)
> - The deployment MUST monitor the mounted secret for changes instead of relying on an in-memory copy of the secret read from the mount.
> - When a Tenant-Wide secret is updated, the tenant is responsible for observing the response of /secrets/{secret-name} endpoint to ensure that the Replicator has successfully updated the secret in all resource groups.



<a name="task_cxf_n13_tcc__steps_o4t_ncf_zcc"/>

## Procedure

1.  Send a PATCH request to the endpoint `{{apiurl}}/v2/admin/secrets/{{secretName}}`

    As the request body, select the *raw* radio button and enter the following code:

    > ### Source Code:  
    > ```
    > {
    > 	"data": {
    > 		"updated-credentials": "bXktc2VjcmV0LW90aGVyLWNyZWRlbnRpYWw="
    > 	}
    > }
    > 					
    > ```

    Specify the scope of the request via the header `AI-Tenant-Scope` and specify the scope via the or `AI-Resource-Group`:

    -   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
    -   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

2.  Send the request.




<a name="task_cxf_n13_tcc__result_q22_kgf_cyb"/>

## Results

> ### Output Code:  
> ```
> {
> "message": "The secret has been modified",
> "name": "my-generic-secret"
> }
> ```

