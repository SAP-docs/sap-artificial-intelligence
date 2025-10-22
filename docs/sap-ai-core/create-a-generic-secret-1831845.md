<!-- loio1831845910364e97b3a7c6644a9e1f4b -->

# Create a Generic Secret

A generic secret authorizes SAP AI Core to use your resource group without exposing your credentials.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__prereq_ny2_dbd_gyb"/>

## Prerequisites

You've completed the initial setup. For more information, see [Initial Setup](initial-setup-38c4599.md).

You have access to a public-facing Docker registry over the internet. It isn't possible to use a Docker registry behind a VPN or corporate network.



<a name="task_i3h_n13_tcc__context_lm3_sy2_zcc"/>

## Context

Generic secrets store sensitive information when system secrets aren't applicable. They're useful in integration scenarios where SAP AI Core acts as an orchestration layer.

> ### Remember:  
> You are responsible for the rotation of your access credentials and certificates of SAP AI Core within BTP according to regional policy.

SAP AI Core lets you use generic secrets at various levels:

-   Main-tenant scope

-   Tenant-wide level

-   Resource-group level


Generic secrets differ from system secrets, like those for object stores or Docker registries. They store sensitive information for the main tenant, all resource groups, or individual resource groups via an API. You can attach these secrets to containers in executions or deployments as environment variables or volume mounts.

To allow the rotation of tenant-wide secrets for long-running deployments without requiring a restart, the deployment must mount the tenant-wide secret. It must also monitor the mounted secret for changes instead of relying on an in-memory copy. When a tenant-wide secret is updated, the tenant must observe the `resourceGroupSecretReplicationStatus` field in the `Get Secret` endpoint to confirm that the secret has been successfully replicated across the required resource groups. For more information, see [Consume Generic Secrets in Executions or Deployments](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/185a3245692542a78bfeff87220410c6.html).

Each tenant can have a maximum of five tenant-wide secrets. If you reach this limit, you receive an error message. To free up space, delete tenant-wide secrets as described at [Delete a Generic Secret](delete-a-generic-secret-d5d5187.md). Alternatively, submit a ticket to request an increase in your quota.

> ### Tip:  
> Generic secrets created at the tenant level automatically propagate to all resource groups. However, if a generic secret with the same name is created at the resource-group level, it replaces the tenant-level secret at the time of creation. The system periodically overrides resource-group level secrets with the corresponding tenant-level secret, but this process can take some time. If a resource-group user creates a secret with the same name as an existing tenant-wide secret, it temporarily overwrites the tenant-wide secret at the resource-group level. This behavior can cause issues, especially for critical operations such as metering.
> 
> To prevent unintended overwrites, ensure that the tenant prevents resource-group users from creating arbitrary secrets. You can do so in the following ways:
> 
> -   Restrict users at resource-group level from accessing the `secrets` endpoint by withholding the JWT token.
> -   Allow users at resource-group level to create generic secrets by making a request using a different authentication mechanism. The main tenant can then validate and transform these requests before propagating them to the runtime adapter, ensuring that secret names remain consistent and critical secrets aren't unintentionally modified.



<a name="task_i3h_n13_tcc__steps_mm3_sy2_zcc"/>

## Procedure

Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
-   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

```
curl --location --request POST "$AI_API_URL/v2/admin/secrets" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--header 'AI-Resource-Group: default' \
--data-raw '{
	"name": "MY_GENERIC_SECRET",
	"data": {
		"some-credential": "bXktc2Vuc2l0aXZlLWRhdGE="
			}
}'					
```

> ### Note:  
> The secret name is written without hyphens to make it simple to consume as a Unix environment variable later. It is written in capitals as is convention.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__prereq_pkr_zhd_gyb"/>

## Prerequisites

You've completed the initial setup. For more information, see [Initial Setup](initial-setup-38c4599.md).

You have access to a public-facing Docker registry over the internet. It isn't possible to use a Docker registry behind a VPN or corporate network.



<a name="task_cxf_n13_tcc__context_rw3_ry2_zcc"/>

## Context

Generic secrets store sensitive information when system secrets aren't applicable. They're useful in integration scenarios where SAP AI Core acts as an orchestration layer.

> ### Remember:  
> You are responsible for the rotation of your access credentials and certificates of SAP AI Core within BTP according to regional policy.

SAP AI Core lets you use generic secrets at various levels:

-   Main-tenant scope

-   Tenant-wide level

-   Resource-group level


Generic secrets differ from system secrets, like those for object stores or Docker registries. They store sensitive information for the main tenant, all resource groups, or individual resource groups via an API. You can attach these secrets to containers in executions or deployments as environment variables or volume mounts.

To allow the rotation of tenant-wide secrets for long-running deployments without requiring a restart, the deployment must mount the tenant-wide secret. It must also monitor the mounted secret for changes instead of relying on an in-memory copy. When a tenant-wide secret is updated, the tenant must observe the `resourceGroupSecretReplicationStatus` field in the `Get Secret` endpoint to confirm that the secret has been successfully replicated across the required resource groups. For more information, see [Consume Generic Secrets in Executions or Deployments](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/185a3245692542a78bfeff87220410c6.html).

Each tenant can have a maximum of five tenant-wide secrets. If you reach this limit, you receive an error message. To free up space, delete tenant-wide secrets as described at [Delete a Generic Secret](delete-a-generic-secret-d5d5187.md). Alternatively, submit a ticket to request an increase in your quota.

> ### Tip:  
> Generic secrets created at the tenant level automatically propagate to all resource groups. However, if a generic secret with the same name is created at the resource-group level, it replaces the tenant-level secret at the time of creation. The system periodically overrides resource-group level secrets with the corresponding tenant-level secret, but this process can take some time. If a resource-group user creates a secret with the same name as an existing tenant-wide secret, it temporarily overwrites the tenant-wide secret at the resource-group level. This behavior can cause issues, especially for critical operations such as metering.
> 
> To prevent unintended overwrites, ensure that the tenant prevents resource-group users from creating arbitrary secrets. You can do so in the following ways:
> 
> -   Restrict users at resource-group level from accessing the `secrets` endpoint by withholding the JWT token.
> -   Allow users at resource-group level to create generic secrets by making a request using a different authentication mechanism. The main tenant can then validate and transform these requests before propagating them to the runtime adapter, ensuring that secret names remain consistent and critical secrets aren't unintentionally modified.



<a name="task_cxf_n13_tcc__steps_sw3_ry2_zcc"/>

## Procedure

1.  Send a POST request and enter the URL `{{apiurl}}/v2/admin/secrets`.

2.  As the request body, select the *raw* radio button and enter your credentials in JSON format:

    ```
    {
    "name": "MY_GENERIC_SECRET",
    "data": {
    		"some-credential": "bXktc2VjcmV0LWNyZWRlbnRpYWw=",
    		"other-credentials": "bXktc2VjcmV0LW90aGVyLWNyZWRlbnRpYWw="
    		}
    }
    ```

    -   `name`: Set the name of your generic secret.
    -   `data`: Enter a JSON string that represents your generic secret.

    > ### Note:  
    > The secret name is written without hyphens to make it simple to consume as a Unix environment variable later. It is written in capitals as is convention.

3.  Specify the scope of the request via the header `AI-Tenant-Scope` and `AI-Resource-Group`:

    -   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
    -   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

    In this example, we are using the resource-group level.


    <table>
    <tr>
    <th valign="top">

    Key
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    AI-Resource-Group
    
    </td>
    <td valign="top">
    
    <Your resource group name\>
    
    </td>
    </tr>
    </table>
    
4.  Send the request.




<a name="task_cxf_n13_tcc__result_fxd_cmf_cyb"/>

## Results

> ### Output Code:  
> ```
> {
> "message": "secret has been created",
> "name": "MY_GENERIC_SECRET"
> }
> ```

