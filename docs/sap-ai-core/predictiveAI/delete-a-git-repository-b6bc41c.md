<!-- loiob6bc41cbd72d49479ea722b546826259 -->

# Delete a Git Repository

You remove a Git repository from a connection if its URL is invalid or contains errors, or if the repo is no longer required. Once a Git repository is removed, it can no longer be selected as a source repository for an application.



<a name="loiob6bc41cbd72d49479ea722b546826259__section_m1h_pvs_hvb"/>

## Using a Third-Party API Platform

Send a DELETE request to the endpoint `{{apiurl}}/v2/admin/repositories/{{repositoryName}}` and include your repository name.



<a name="loiob6bc41cbd72d49479ea722b546826259__section_tpw_mws_hvb"/>

## Using curl

```
curl --location --request DELETE "{{apiurl}}/v2/admin/repositories/{{repositoryName}}" \

```

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



## Context

You remove a Git repository from a connection if its URL is invalid or contains errors, or if the repository is no longer required. Once a Git repository is removed, it can no longer be selected as a source repository for an application.



<a name="task_i3h_n13_tcc__steps_pvs_nfc_wcc"/>

## Procedure

Run the following code:

```
curl --location --request DELETE "{{apiurl}}/v2/admin/repositories/{{repositoryName}}" \

```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__context_zyt_rgc_wcc"/>

## Context

You remove a Git repository from a connection if its URL is invalid or contains errors, or if the repository is no longer required. Once a Git repository is removed, it can no longer be selected as a source repository for an application.



<a name="task_cxf_n13_tcc__steps_azt_rgc_wcc"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/admin/repositories/{{repositoryName}}` and include your repository name.

