<!-- loioc8cd25115c124444a6f9a28f1cb8228d -->

# Add a Git Repository

As a system administrator, you can add Git repositories which can be used within your training and serving processes.



<a name="loioc8cd25115c124444a6f9a28f1cb8228d__prereq_jxh_cq2_rob"/>

## Prerequisites

You have the `aicore_admin_repositories_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).

You have created the required AI API connection using the *Workspaces* app. See [Add Connection to SAP AI Core](add-connection-to-sap-ai-core-71dfe2c.md).

You have access to the Git repository over the Internet.



## Context

You can add multiple Git repositories for a selected connection. The Git repository must already exist with valid authentication details.

> ### Note:  
> SAP AI Core supports the use of Git repositories; the use of other private or open source repositories is not supported.



## Procedure

1.  In the *Workspaces* app, choose the AI API connection.

2.  Open the *SAP AI Core Administration* app and choose *Git Repositories*.

    The *Git Repositories* screen appears with details of any existing repositories, including name, status, and URL.

3.  Choose *Add* to enter reference details for a new repository.

4.  Complete the fields in the *Add a Git Repository* dialog box as follows:

    1.  Enter a URL for the repository.

    2.  Enter a name for the repository.

        Repository names must comply with the following criteria:

        -   Contain only lowercase alphanumeric characters, hyphens \(-\), or periods \(.\)

        -   Start with an alphanumeric character

        -   End with an alphanumeric character


    3.  Enter a user name and access token.

        The combination of user name and access token enables read access to the repo.


5.  Choose *Add* to add the repo to the available repositories for the selected SAP AI Core connection.




<a name="loioc8cd25115c124444a6f9a28f1cb8228d__result_upp_yr4_xsb"/>

## Results

The new repo appears on the *Git Repositories* screen. The onboarding status for the new repo is *In progress* until the authorization details are authenticated.

![Git repository overview with new repo created.](images/Image_AIL_Git_repo_71f5439.png)

**Related Information**  


[Add Connection to SAP AI Core](add-connection-to-sap-ai-core-71dfe2c.md "As an administrator, you can add multiple connections to different instances of SAP AI Core. You can enter the service key details for a connection manually, or upload a service key file.")

[Setting Up Your Git Repository](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3269092e37d141a293f0dbd7eaafc829.html)

