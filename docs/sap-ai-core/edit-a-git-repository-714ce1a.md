<!-- loio714ce1af1b0f4e3981e3d32d2c593cf9 -->

# Edit a Git Repository



<a name="loio714ce1af1b0f4e3981e3d32d2c593cf9__section_m1h_pvs_hvb"/>

## Using Postman

Send a PATCH request to the endpoint `{{apiurl}}/v2/admin/repositories/{{repositoryName}}` and include your changes in the body.



<a name="loio714ce1af1b0f4e3981e3d32d2c593cf9__section_tpw_mws_hvb"/>

## Using curl

Submit a PATCH request to the endpoint <code><code>{{apiurl}}/v2/admin/repositories</code></code> and include your changes:

```
curl --location --request PATCH "$AI_API_URL/v2/admin/repositories" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--data-raw '{
        "url": "https://github.com/john/examplerepo",
        "username": "john",
        "password": "<GIT_PAT_USER_TOKEN>"
    }'

```



You specify your unique git repository details as follows:

-   `url`: URL of the git repository

-   `username`: \(Service\) user that is accessing the git repository

-   `password`: git personal access token. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


