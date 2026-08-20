<!-- loiob6681769f191490f8832d3fbb6794e89 -->

# Add a Git Repository

You can use your own git repository to version control your SAP AI Core templates.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using the API



<a name="task_i3h_n13_tcc__prereq_lq4_g1p_kxkkbk"/>

## Prerequisites

-   You've completed the initial setup.

-   You have access to a git repository over the Internet.
-   You've generated a personal access token for your git repository. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
-   If you want to onboard a git repository hosted on GitLab, make sure that the repository URL contains the `.git` suffix.
-   Secrets aren't permitted in your repository. If secrets are used, it isn't possible to synchronize content.

> ### Note:  
> When you synchronize resources, make sure that there are no naming collisions, especially if you use multiple repositories or applications in one tenant. If you experience difficulties during synchronization, we recommend that you use only one repository or application per tenant.
> 
> For example, the following repository URLs are all considered the same repository:
> 
> -   `https://github.com/user/repo`
> -   `https://github.com/user/repo/`
> -   `https://github.com/user/REPO/`



<a name="task_i3h_n13_tcc__context_s5h_dbp_kkkxbk"/>

## Context

Git repositories are managed by creating personal access tokens and adding them in SAP AI Core. Personal access tokens are a means of allowing and controlling connections to GitHub repositories without compromising your credentials.

> ### Remember:  
> You are responsible for the rotation of your access credentials and certificates of SAP AI Core within BTP according to regional policy.



<a name="task_i3h_n13_tcc__steps_ryt_dy1_wcc"/>

## Procedure

Submit a POST request to the endpoint <code><code>$AI_API_URL/v2/admin/repositories</code> </code> and include your credentials in your request.

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

-   Repository name \(optional\)
-   Your credentials

```
curl --location --request POST "$AI_API_URL/v2/admin/repositories" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "<yourChoiceOfRepositoryName>",
    "url": "https://github.com/john/examplerepo",   
    "username": "john",
    "password": "<GIT_PAT_USER_TOKEN>"
}'

```

You specify your unique git repository details as follows:

-   `url`: URL of the git repository

    > ### Restriction:  
    > -   Only ASCII alphanumerics, digits, and the characters “.”, “ -”, “\_” and “%” are allowed.
    > -   Do not use IP addresses as repository URLs.

-   `username`: \(Service\) user that’s accessing the git repository

-   `password`: git personal access token. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


> ### Tip:  
> To share a repository between two tenants, add the repository in SAP AI Core separately for each tenant and provide the **same** `username` and `password`.



## Results

Successful responses return code **200** and include a success message and ID.

> ### Output Code:  
> ```
> {
>   "id": "<yourRepositoryId>",
>   "message": "The repository has been on-boarded"
> }
> ```

**Related Information**  


[Initial Setup](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/38c4599432d74c1d94e70f7c955a717d.html "Get started with SAP AI Core using the standard procedures for the SAP BTP, Cloud Foundry environment or Kyma environment.") :arrow_upper_right:

