<!-- loiobee001a0afb54f82858038a140514a49 -->

# Delete an Object Store Secret

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__context_kqh_hhy_ycc"/>

## Context

Deleting an object store secret stops access to the object store.



<a name="task_i3h_n13_tcc__steps_lqh_hhy_ycc"/>

## Procedure

Run the following code:

```
curl --location --request DELETE "$AI_API_URL/v2/admin/objectStoreSecrets/{{objectStoreName}}" \ 
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__context_sw5_chy_ycc"/>

## Context

Deleting an object store secret stops access to the object store.



<a name="task_cxf_n13_tcc__steps_tw5_chy_ycc"/>

## Procedure

Send a DELETE request to the endpoint

