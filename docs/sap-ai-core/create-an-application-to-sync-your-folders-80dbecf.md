<!-- loio80dbecf3bc224ef5a300ba214de07973 -->

# Create an Application to Sync Your Folders

After you have registered your git repository and created any required secrets, you need to create an application to sync the templates in your repository. It will take some time for your application to sync with the git repository, but you can check the status of the application to see when synchronization is complete.



<a name="loio80dbecf3bc224ef5a300ba214de07973__section_enm_1dy_lvb"/>

## Using Postman



### Procedure

Use the endpoint `{{apiurl}}/v2/admin/applications` to create an application that syncs templates from your git repository:![](images/AIC_e69cb44.png)

-   `applicationName`: Set a name for your application. The name must be between 3 and 64 characters long and match ***\[A-Za-z0-9\\-\\\_\]+***.

-   `repositoryUrl`: The URL of a registered git repository.

-   `revision`: The revision to target.

-   `path`: The path to the target folder that contains the templates to be synced.


Since each application points to a particular path and revision in the repository, multiple applications may be created for the same `repositoryUrl`.



### Results

After the GitOps setup is completed, the templates in your git repository are automatically synced to SAP AI Core at ~3 minute intervals.



### Next Steps

Check the synchronization status of your application by submitting a GET request to `{{apiurl}}/v2/admin/applications/{{appName}}/status`:

![](images/AIC_32091f0.png)

As `applicationName`, enter the name of your application that you specified when you created the application.



<a name="loio80dbecf3bc224ef5a300ba214de07973__section_e2w_mgy_lvb"/>

## Using curl

Use the endpoint `{{apiurl}}/v2/admin/applications` to create an application that syncs templates from your git repository:

```
curl --location --request POST "[/pandoc/div/div/horizontalrule/codeblock/span/code
     {"filepath"}) $AI_API_URL/v2/admin/applications (code]" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--data-raw '{
        "applicationName": "my-app",
        "repositoryUrl": "https://github.com/john/examplerepo",
        "revision": "HEAD",
        "path": "workflows"
    }'
```

-   `applicationName`: Set a name for your application. The name must be between 3 and 64 characters long and match ***\[A-Za-z0-9\\-\\\_\]+***.

-   `repositoryUrl`: The URL of a registered git repository.

-   `revision`: The revision to target.

-   `path`: The path to the target folder that contains the templates to be synced.


Since each application points to a particular path and revision in the repository, multiple applications may be created for the same `repositoryUrl`.



### Results

After the GitOps setup is completed, the templates in your git repository are automatically synced to SAP AI Core at ~3 minute intervals.



### Next Steps

Check the synchronization status of your application by submitting a GET request to `{{apiurl}}/v2/admin/applications/{{appName}}/status`:

```
curl --location --request GET "[/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/code
     {"filepath"}) $AI_API_URL/v2/admin/applications/{{appName}}/status (code]" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json'
```

As `applicationName`, enter the name of your application that you specified when you created the application.



<a name="loio80dbecf3bc224ef5a300ba214de07973__section_m4l_4cy_3wX"/>

## Sync an Application Manually



### Applications sync with your GitHub repository automatically at intervals of ~3 minutes. Use the endpoint below to manually request a sync:

`{{apiurl}}/admin/applications/{{appName}}/refresh`

**Parent topic:** [Manage Your Git Repository](manage-your-git-repository-2cd2996.md "You can use your own git repository to version control your SAP AI Core templates. The GitOps onboarding to SAP AI Core instances involves setting up your git repository and synchronizing your content.")

**Next:** [Register Your Git Repository and Secrets](register-your-git-repository-and-secrets-b668176.md "Git repositories are managed by creating personal access tokens registering them in SAP AI Core. Personal access tokens are a means of allowing and controlling connections to GitHub repositories without compromising your credentials.")

