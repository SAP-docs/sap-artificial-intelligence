<!-- loiob6bc41cbd72d49479ea722b546826259 -->

# Delete a Git Repository

You remove a Git repository from a connection if its URL is invalid or contains errors, or if the repo is no longer required. Once a Git repository is removed, it can no longer be selected as a source repository for an application.



<a name="loiob6bc41cbd72d49479ea722b546826259__section_m1h_pvs_hvb"/>

## Using Postman

Send a DELETE request to the endpoint `{{apiurl}}/v2/admin/repositories/{{repositoryName}}` and include your repository name.



<a name="loiob6bc41cbd72d49479ea722b546826259__section_tpw_mws_hvb"/>

## Using curl

```
curl --location --request DELETE "{{apiurl}}/v2/admin/repositories/{{repositoryName}}" \

```

