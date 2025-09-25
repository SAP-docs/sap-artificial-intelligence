<!-- loiob5d597051e494b49a4907470f1b238af -->

# Update a Generic Secret

To update a generic secret, use the PATCH endpoint as shown below. The PATCH operation updates the data and/or labels provided. This can be used for rotating secret credentials.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__context_l4b_qcf_zcc"/>

## Context

Generic secrets store sensitive information when system secrets aren't applicable. They're useful in integration scenarios where SAP AI Core acts as an orchestration layer.

SAP AI Core lets you use generic secrets at various levels:

-   Main-tenant scope

-   Tenant-wide level

-   Resource-group level


Generic secrets differ from system secrets, like those for object stores or Docker registries. They store sensitive information for the main tenant, all resource groups, or individual resource groups via an API. You can attach these secrets to containers in executions or deployments as environment variables or volume mounts.

To allow the rotation of tenant-wide secrets for long-running deployments without requiring a restart, the deployment must mount the tenant-wide secret. It must also monitor the mounted secret for changes instead of relying on an in-memory copy. When a tenant-wide secret is updated, the tenant must observe the `resourceGroupSecretReplicationStatus` field in the `Get Secret` endpoint to confirm that the secret has been successfully replicated across the required resource groups. For more information, see [Consume Generic Secrets in Executions or Deployments](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/185a3245692542a78bfeff87220410c6.html).



<a name="task_i3h_n13_tcc__steps_m4b_qcf_zcc"/>

## Procedure

Submit a PATCH request to the endpoint `/v2/admin/secrets/"$SECRET_NAME"`. Specify the scope via the headers:

Specify the scope of the request via the header `AI-Tenant-Scope` and specify the scope via the or `AI-Resource-Group`:

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
		"labels": [
			{"key": "ext.ai.sap.com/<key1>", "value": "<value1>"},
			{"key": "ext.ai.sap.com/<key2>", "value": "<value2>"}
			]
}'
```



<a name="task_i3h_n13_tcc__result_wgs_ylt_ngc"/>

## Results

> ### Output Code:  
> ```
> {
> "message": "The secret has been modified",
> "name": "my-generic-secret"
> }
> ```

The response confirms the successful update of the secret. Label updates are applied immediately without requiring secret recreation. You can verify label updates by retrieving the secret using the GET endpoint.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__context_n4t_ncf_zcc"/>

## Context

Generic secrets store sensitive information when system secrets aren't applicable. They're useful in integration scenarios where SAP AI Core acts as an orchestration layer.

SAP AI Core lets you use generic secrets at various levels:

-   Main-tenant scope

-   Tenant-wide level

-   Resource-group level


Generic secrets differ from system secrets, like those for object stores or Docker registries. They store sensitive information for the main tenant, all resource groups, or individual resource groups via an API. You can attach these secrets to containers in executions or deployments as environment variables or volume mounts.

To allow the rotation of tenant-wide secrets for long-running deployments without requiring a restart, the deployment must mount the tenant-wide secret. It must also monitor the mounted secret for changes instead of relying on an in-memory copy. When a tenant-wide secret is updated, the tenant must observe the `resourceGroupSecretReplicationStatus` field in the `Get Secret` endpoint to confirm that the secret has been successfully replicated across the required resource groups. For more information, see [Consume Generic Secrets in Executions or Deployments](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/185a3245692542a78bfeff87220410c6.html).



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
    > 	"labels": [
    > 			{"key": "ext.ai.sap.com/<key1>", "value": "<value1>"},
    > 			{"key": "ext.ai.sap.com/<key2>", "value": "<value2>"}
    > 			]
    > }
    > 					
    > ```

    Specify the scope of the request via the header `AI-Tenant-Scope` and specify the scope via the or `AI-Resource-Group`:

    -   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
    -   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

    You can update labels alongside or instead of secret data. Only labels with the `ext.ai.sap.com/` prefix can be modified.

    > ### Restriction:  
    > The following labels cannot be updated via PATCH:
    > 
    > -   `ext.ai.sap.com/document-grounding`
    > -   `ext.ai.sap.com/documentRepositoryType`

    To remove a label, set its value to an empty string \(""\).

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

The response confirms the successful update of the secret. Label updates are applied immediately without requiring secret recreation. You can verify label updates by retrieving the secret using the GET endpoint.

