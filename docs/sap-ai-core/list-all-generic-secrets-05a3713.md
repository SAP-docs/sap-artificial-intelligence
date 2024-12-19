<!-- loio05a3713aa6a94356b08e09e86260b16d -->

# List All Generic Secrets



<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_p1m_clf_zcc"/>

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



<a name="task_i3h_n13_tcc__result_vck_3lf_zcc"/>

## Results

The response includes a list of generic secrets, their name, and their creation timestamp. No sensitive information is revealed in the response.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using Postman



<a name="task_cxf_n13_tcc__steps_bqv_vkf_zcc"/>

## Procedure

Send a GET request to the endpoint `{{apiurl}}/v2/admin/secrets`.

1.  As the request body, select the *none* radio button.

2.  Specify the scope of the request via the header `AI-Tenant-Scope` or `AI-Resource-Group`:

    -   `AI-Tenant-Scope` : `true`. The operation will be performed at the main-tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.
    -   `AI-Tenant-Scope` : `true` and `AI-Resource-Group`: `*`. The operation will be performed at the tenant-wide level.




<a name="task_cxf_n13_tcc__result_sxh_jlf_zcc"/>

## Results

The response includes a list of generic secrets, their name, and their creation timestamp. No sensitive information is revealed in the response.

