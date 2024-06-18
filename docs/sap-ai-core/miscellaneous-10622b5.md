<!-- loio10622b5a7e5c449d8b138809c3adc452 -->

# Miscellaneous



<a name="loio10622b5a7e5c449d8b138809c3adc452__section_rxh_yqk_vsb"/>

## 403 - forbidden: RBAC Access denied

When you submit a POST request for an execution or a configuration, you get the error ***403 - forbidden: RBAC Access denied***.



### Check the following:

1.  Check that you are passing the correct `token` and `ai-resource-group header`.
2.  Check your tenant provisioning.



<a name="loio10622b5a7e5c449d8b138809c3adc452__section_qwf_zmk_vsb"/>

## You get a runtime adapter exception

You get the error: ***"Runtime Adapter Exception; Failed to post deployments : \{\\n \\"code\\": \\"400\\",\\n \\"message\\": \\"Missing input parameter or artifacts, one or more placeholder values are not resolved in the serving spec and error is 'dict object' has no attribute ''.\\"\\n\}\\n"***



### Check the following:

Check that your input artifact key doesn't contain any separators, such as “example-artifact-key”. If it does, rename the key \(for example, “exampleArtifactKey”\)



<a name="loio10622b5a7e5c449d8b138809c3adc452__section_amc_xqk_vsb"/>

## You have pushed your template to your GitHub repository but you can't see the executable created via the API



### There may be an error in your template. Check the following:

-   Serving templates always expect an input parameter to be configured. If you don’t have a parameter in your Serving template, add a dummy parameter and create a configuration for it.
-   Hyphens \(-\) are the only separator as permitted in the template name.



<a name="loio10622b5a7e5c449d8b138809c3adc452__section_g2h_yqk_vsb"/>

## You have created a scenario in a template but you cannot see it in the AI API calls



### Use the following solution:

Add a workflow template with the new `scenario_id` \(not a serving template\) to make the scenario visible.



<a name="loio10622b5a7e5c449d8b138809c3adc452__section_nfv_yqk_vsb"/>

## Error: getaddrinfo ENOTFOUND



### Check the following:

1.  Check that all environment variables match your SAP AI Core service keys. Specifically, check:
    -   `auth_url`

    -   `client_id`

    -   `client_secret`

    -   `apiurl`


2.  Submit a GET request to the endpoint `{{apiurl}}/v2/admin/repositories`
3.  If the issue persists, contact SAP support as described at [Monitoring and Troubleshooting](monitoring-and-troubleshooting-f559038.md).



<a name="loio10622b5a7e5c449d8b138809c3adc452__section_q12_chm_vsb"/>

## Git repo doesn't synchronize with SAP AI Core instances.

When you try to synchronize your git repository with SAP AI Core, the response shows empty fields.



### Check the following:

1.  Check that you are using a GitHub personal access token and not your GitHub password.

If you are already using a personal access token, proceed as follows:

1.  Delete all UNKNOWN applications from your SAP AI Core instance using the endpoint:

    DELETE `{{apiurl}}/v2/admin/applications/{{appName}}`

2.  Offboard your GitHub repo from SAP AI Core by calling the endpoint:

    DELETE `{{apiurl}}/v2/admin/repositories/{{repositoryName}}`

3.  Generate a GitHub personal access token and use it to onboard your git repo to SAP AI Core as before. For more information, see [Creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
4.  Sync your application again.

**Parent topic:**[Troubleshooting](troubleshooting-3da90ba.md "For troubleshooting information, see the following sections:")

**Related Information**  


[Repository](repository-fcad603.md "")

[Configuration](configuration-047fad5.md "")

[Artifacts](artifacts-c655daa.md "")

[Application](application-7f1e35b.md "")

[Execution](execution-5ccde4d.md "")

[Docker](docker-1945aa4.md "")

[Deployment](deployment-a10fa8a.md "")

