<!-- loio5ff30f0332b8452d97ed77edf746714a -->

# Delete a Docker Registry Secret

Deleting a docker registry secret removes access to the docker registry.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_f2s_w52_zcc"/>

## Procedure

Submit a DELETE request to the endpoint `$AI_API_URL/v2/admin/dockerRegistrySecrets/{{dockerRegistryName}}`.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_alr_t52_zcc"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/admin/dockerRegistrySecrets/{{dockerRegistryName}}`

