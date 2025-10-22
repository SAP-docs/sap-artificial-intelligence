<!-- loiob6681769f191490f8832d3fbb6794e89 -->

# Add a Git Repository

You can use your own git repository to version control your SAP AI Core templates. The GitOps onboarding to SAP AI Core instances involves setting up your git repository and synchronizing your content.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__prereq_lq4_g1p_kxkkbk"/>

## Prerequisites

-   You have access to a git repository over the Internet.
-   You've generated a personal access token for your git repository. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
-   If you want to onboard a git repository hosted on GitLab, make sure that the repository URL contains the `.git` suffix.
-   Secrets aren't permitted in your repository. If secrets are used, it isn't possible to synchronize content.

-   You've completed the initial setup. For more information, see [Initial Setup](initial-setup-38c4599.md).


> ### Note:  
> When you synchronize resources, make sure that there are no naming collisions, especially if you use multiple repositories or applications in one tenant. If you experience difficulties during synchronization, we recommend that you use only one repository or application per tenant.



<a name="task_i3h_n13_tcc__context_s5h_dbp_kkkxbk"/>

## Context

Git repositories are managed by creating personal access tokens and registering them in SAP AI Core. Personal access tokens are a means of allowing and controlling connections to GitHub repositories without compromising your credentials.

> ### Remember:  
> You are responsible for the rotation of your access credentials and certificates of SAP AI Core within BTP according to regional policy.



<a name="task_i3h_n13_tcc__steps_ryt_dy1_wcc"/>

## Procedure

Submit a POST request to the endpoint <code><code>{{apiurl}}/v2/admin/repositories</code></code> and include your credentials:

```
curl --location --request POST "$AI_API_URL/v2/admin/repositories" \
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

-   `username`: \(Service\) user that’s accessing the git repository

-   `password`: git personal access token. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


> ### Tip:  
> To share a repository between two tenants, register the repository in SAP AI Core separately for each tenant and provide the **same** `username` and `password`.



<a name="task_i3h_n13_tcc__postreq_cdx_fz1_wcc"/>

## Next Steps

Create an application to sync your folders. For more information, see [Create an Application](create-an-application-80dbecf.md).

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__prereq_lq4_g1p_kxkb"/>

## Prerequisites

-   You have access to a git repository over the Internet.
-   You've generated a personal access token for your git repository. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
-   If you want to onboard a git repository hosted on GitLab, make sure that the repository URL contains the `.git` suffix.
-   Secrets aren't permitted in your repository. If secrets are used, it isn't possible to synchronize content.

-   You've completed the initial setup. For more information, see [Initial Setup](initial-setup-38c4599.md).


> ### Note:  
> When you synchronize resources, make sure that there are no naming collisions, especially if you use multiple repositories or applications in one tenant. If you experience difficulties during synchronization, we recommend that you use only one repository or application per tenant.



<a name="task_cxf_n13_tcc__context_s5h_dbp_kkxktbk"/>

## Context

Git repositories are managed by creating personal access tokens and registering them in SAP AI Core. Personal access tokens are a means of allowing and controlling connections to GitHub repositories without compromising your credentials.

> ### Remember:  
> You are responsible for the rotation of your access credentials and certificates of SAP AI Core within BTP according to regional policy.



<a name="task_cxf_n13_tcc__steps_cyl_cy1_wcc"/>

## Procedure

Send a POST request to the endpoint `{{apiurl}}/v2/admin/repositories` and include your credentials in JSON format in the *raw* body:

You specify your unique git repository details as follows:

-   `url`: URL of the git repository

-   `username`: \(Service\) user that’s accessing the git repository

-   `password`: git personal access token. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


> ### Tip:  
> To share a repository between two tenants, register the repository in SAP AI Core separately for each tenant and provide the **same** `username` and `password`.



<a name="task_cxf_n13_tcc__postreq_odh_gz1_wcc"/>

## Next Steps

Create an application to sync your folders. For more information, see [Create an Application](create-an-application-80dbecf.md).

