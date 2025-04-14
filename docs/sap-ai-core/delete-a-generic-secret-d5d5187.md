<!-- loiod5d5187da4d2483baa6a203f1bcbe33a -->

# Delete a Generic Secret

To get a secret name, see [Get Generic Secrets](get-generic-secrets-05a3713.md).

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_azz_3kf_zcc"/>

## Procedure

Submit a DELETE request to the endpoint `/v2/admin/secrets/"$SECRET_NAME"`. Specify the scope of the request via the header `AI-Tenant-Scope` and `AI-Resource-Group`:

-   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
-   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
-   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

In this example we use the resource-group scope:

```
curl --location --request DELETE "$AI_API_URL/v2/admin/secrets/$SECRET_NAME$AI_API_URL/v2/admin/secrets/$SECRET_NAME" \
--header "Authorization: Bearer $TOKEN" \
--header 'AI-Resource-Group: default' 

```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_mvt_hkf_zcc"/>

## Procedure

1.  Send a DELETE request to the endpoint`{{apiurl}}/v2/admin/secrets/{{secretName}}`

    As the request body, select the *none* radio button. Specify the scope of the request via the header `AI-Tenant-Scope` or `AI-Resource-Group`:

    -   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
    -   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.

2.  Send the request.




<a name="task_cxf_n13_tcc__result_gf3_ggf_cyb"/>

## Results

> ### Output Code:  
> ```
> 200
> ```

