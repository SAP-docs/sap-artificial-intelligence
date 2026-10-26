<!-- loio714ce1af1b0f4e3981e3d32d2c593cf9 -->

# Edit a Git Repository

You can edit a Git repository using its name to update your authentication details. This lets you maintain secure access and keep workflows synced with the latest code.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using the API



<a name="task_i3h_n13_tcc__steps_ahz_24b_wcc"/>

## Procedure

Submit a PATCH request to the endpoint <code><code>$AI_API_URL/v2/admin/repositories/$REPOSITORY_NAME</code></code> and include your changes.

Make sure that you've set the following headers:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $AUTH\_TOKEN

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. You can set the URL as an environment variable.

</td>
</tr>
</table>

Populate your request with the following:

-   Repository name
-   Updates to your credentials

```
curl --location --request PATCH "$AI_API_URL/v2/admin/repositories/$REPOSITORY_NAME" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--data-raw '{
        "username": "john",
        "password": "<GIT_PAT_USER_TOKEN>"
    }'

```



## Results

Successful responses return code **200** and include a success message and ID.

> ### Output Code:  
> ```
> {
>   "id": "<yourRepositoryId>",
>   "message": "The repository credentials have been updated and will eventually be synced"
> }
> ```

