<!-- loio05a3713aa6a94356b08e09e86260b16d -->

# Get Generic Secrets

Generic secrets can either be retrieved as a single secret, or you can list all existing secrets.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Get a Secret Using Curl



<a name="task_i3h_n13_tcc__steps_p1m_clf_zcc"/>

## Procedure

Submit a GET request to the endpoint `/v2/admin/secrets/<secret-name>`, and include the scope via the headers:

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
-   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

```
curl --location --request GET "$AI_API_URL/v2/admin/secrets/$SECRET_NAME" \
--header "Authorization: Bearer $TOKEN" \
--header 'AI-Resource-Group: default'

```



<a name="task_i3h_n13_tcc__result_vck_3lf_zcc"/>

## Results

The response contains the name, and the creation timestamp of the requested generic secrets. No sensitive information is revealed in the response.

In the case of a tenant-wide secret, the response additionally includes a list of all resource groups associated with the tenant and the current replication status of the secret to these resource groups.

> ### Output Code:  
> ```
> {
>   "name": "secret-1",
>   "createdAt": "<timestamp>",
>   "resourceGroupSecretReplicationStatus":{
>       "rg-id-1" : true,  # secret was replicated correctly in this namespace
>       "rg-id-2" : false, # secret was not replicated or does not exist in this namespace yet
>   }
> }
> # Example response for tenant-scoped or resource group level secrets:
> {
>   "name": "secret-1",
>   "createdAt": "<timestamp>"
> }
> ```

<a name="task_zmk_l3m_22c"/>

<!-- task\_zmk\_l3m\_22c -->

## Get All Secrets Using Curl



## Procedure

Submit a GET request to the endpoint `/v2/admin/secrets`, and include the scope via the headers:

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
-   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

```
curl --location --request GET "$AI_API_URL/v2/admin/secrets" \
--header "Authorization: Bearer $TOKEN" \
--header 'AI-Resource-Group: default'

```



<a name="task_zmk_l3m_22c__result_bnk_l3m_22c"/>

## Results

The response contains the name, and the creation timestamp of the requested generic secrets. No sensitive information is revealed in the response.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Get a Secret Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_bqv_vkf_zcc"/>

## Procedure

Send a GET request to the endpoint `{{apiurl}}/v2/admin/secrets/{{secret_name]]`.

1.  As the request body, select the *none* radio button.

2.  Specify the scope of the request via the header `AI-Tenant-Scope` or `AI-Resource-Group`:

    -   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
    -   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.




<a name="task_cxf_n13_tcc__result_sxh_jlf_zcc"/>

## Results

The response contains the name, and the creation timestamp of the requested generic secrets. No sensitive information is revealed in the response.

In the case of a tenant-wide secret, the response additionally includes a list of all resource groups associated with the tenant and the current replication status of the secret to these resource groups.

> ### Output Code:  
> ```
> {
>   "name": "secret-1",
>   "createdAt": "<timestamp>",
>   "resourceGroupSecretReplicationStatus":{
>       "rg-id-1" : true,  # secret was replicated correctly in this namespace
>       "rg-id-2" : false, # secret was not replicated or does not exist in this namespace yet
>   }
> }
> # Example response for tenant-scoped or resource group level secrets:
> {
>   "name": "secret-1",
>   "createdAt": "<timestamp>"
> }
> ```

<a name="task_imv_l3m_22c"/>

<!-- task\_imv\_l3m\_22c -->

## Get All Secrets Using a Third-Party API Platform



## Procedure

Send a GET request to the endpoint `{{apiurl}}/v2/admin/secrets`.

1.  As the request body, select the *none* radio button.

2.  Specify the scope of the request via the header `AI-Tenant-Scope` or `AI-Resource-Group`:

    -   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
    -   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.




<a name="task_imv_l3m_22c__result_jmv_l3m_22c"/>

## Results

The response includes a list of generic secrets, their name, and their creation timestamp. No sensitive information is revealed in the response.

