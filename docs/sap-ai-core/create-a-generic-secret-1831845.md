<!-- loio1831845910364e97b3a7c6644a9e1f4b -->

# Create a Generic Secret

A generic secret gives SAP AI Core authorization to utilize your resource group without exposing your credentials.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__prereq_ny2_dbd_gyb"/>

## Prerequisites

You have completed the Initial Setup. For more information, see [Initial Setup](initial-setup-38c4599.md).



<a name="task_i3h_n13_tcc__context_lm3_sy2_zcc"/>

## Context

Generic Secrets are used in addition to store sensitive information when system secrets are not applicable, for example in integration use cases where SAP AI Core is an orchestration layer.

SAP AI Core lets you optionally use generic secrets at the following levels:

-   Main-tenant scope

-   Tenant wide level

-   Resource-group level


Generic secrets are different to system secrets \(such as object store, Docker registry, and so on\) and can be used to store sensitive information, either for the main tenant, for all of its resource groups, or for each resource group via an API. The latter can be attached to containers in executions or deployments as environment variables or volume mounts.

Tenant-wide secrets are only automatically propagated to the appropriate resource group when a new execution or deployment is created. They are not propagated to running deployments.

> ### Note:  
> Each tenant can have a maximum of five tenant-wide secrets. If you reach this limit, you'll receive an error message. To free up space, you can delete some tenant-wide secrets as described at [Delete a Generic Secret](delete-a-generic-secret-d5d5187.md). Alternatively, you can submit a ticket to request an increase your quota.



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

## Using Postman



<a name="task_cxf_n13_tcc__prereq_pkr_zhd_gyb"/>

## Prerequisites

You have completed the Initial Setup. For more information, see [Initial Setup](initial-setup-38c4599.md).



<a name="task_cxf_n13_tcc__context_rw3_ry2_zcc"/>

## Context

Generic Secrets are used in addition to store sensitive information when system secrets are not applicable, for example in integration use cases where SAP AI Core is an orchestration layer.

SAP AI Core lets you optionally use generic secrets at the following levels:

-   Main-tenant scope

-   Tenant wide level

-   Resource-group level


Generic secrets are different to system secrets \(such as object store, Docker registry, and so on\) and can be used to store sensitive information, either for the main tenant, for all of its resource groups, or for each resource group via an API. The latter can be attached to containers in executions or deployments as environment variables or volume mounts.

Tenant-wide secrets are only automatically propagated to the appropriate resource group when a new execution or deployment is created. They are not propagated to running deployments.

> ### Note:  
> Each tenant can have a maximum of five tenant-wide secrets. If you reach this limit, you'll receive an error message. To free up space, you can delete some tenant-wide secrets as described at [Delete a Generic Secret](delete-a-generic-secret-d5d5187.md). Alternatively, you can submit a ticket to request an increase your quota.



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

