<!-- loio2cd299632c194b44bf25b4726217fbb9 -->

# Manage Your Git Repository

You can use your own git repository to version control your SAP AI Core templates. The GitOps onboarding to SAP AI Core instances involves setting up your git repository and synchronizing your content.



<a name="loio2cd299632c194b44bf25b4726217fbb9__section_s3p_byx_lvb"/>

## Prerequisites

You have access to a git repository over the Internet.



<a name="loio2cd299632c194b44bf25b4726217fbb9__section_u1k_gyx_lvb"/>

## Context

To make calls to the AI API, you can use Launchpad, Postman or curl.

1.  [Register Your Git Repository and Secrets](register-your-git-repository-and-secrets-b668176.md "Git repositories are managed by creating personal access tokens registering them in SAP AI
									Core. Personal access tokens are a means of allowing and controlling
		connections to GitHub repositories without compromising your credentials.")  
Git repositories are managed by creating personal access tokens registering them in SAP AI Core. Personal access tokens are a means of allowing and controlling connections to GitHub repositories without compromising your credentials.
2.  [Create an Application to Sync Your Folders](create-an-application-to-sync-your-folders-80dbecf.md "After you have registered your git repository and created any required secrets, you need to create an application to sync the templates in
		your repository. It will take some time for your application to sync with the git repository, but you can check the status of the application
		to see when synchronization is complete.")  
After you have registered your git repository and created any required secrets, you need to create an application to sync the templates in your repository. It will take some time for your application to sync with the git repository, but you can check the status of the application to see when synchronization is complete.

**Parent topic:** [Administration](administration-7937fc1.md "Creating secrets for your tools, means that you can connect external programs and tools without compromising your account. The tools can be used to incorporate version control, cloud storage and portable containers.")

**Related Information**  


[Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group represents a unique workspace environment, where users can create or add entities such as configurations, executions, deployments, and artifacts.")

[Manage Object Store Secrets](manage-object-store-secrets-f10b532.md "Connect SAP AI Core to a cloud object store and manage access using an object store secret. The connected storage is used as storage for your dataset, models and other cache files of the Metaflow Library for SAP AI Core.")

[Manage Docker Registry Secrets](manage-docker-registry-secrets-c5445c4.md "Docker facilitates the packaging and running of an application in a remote container. Connect SAP AI Core to a Docker repository and manage access using a Docker registry secret.")

