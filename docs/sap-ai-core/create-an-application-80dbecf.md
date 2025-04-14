<!-- loio80dbecf3bc224ef5a300ba214de07973 -->

# Create an Application

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__context_dh5_p2b_wcc"/>

## Context

After you have registered your git repository, you need to create an application to sync the templates in your repository. The first sync takes some time, but you can check the status of the application to see when it is complete. After the first sync, syncing takes place automatically, every ~3 minutes, or can be requested manually.

-   `applicationName`: Set a name for your application. The name must be between 3 and 64 characters long and match `[A-Za-z0-9\-\_]+`.

-   `repositoryUrl`: The URL of a registered git repository.

-   `revision`: The revision to target. *<HEAD\>* refers to the most recent.

-   `path`: The path to the target folder that contains the templates to be synced.




<a name="task_i3h_n13_tcc__steps_eh5_p2b_wcc"/>

## Procedure

Submit a POST request to the endpoint `{{apiurl}}/v2/admin/applications` including details of your application:

```
curl --location --request POST "$AI_API_URL/v2/admin/applications" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--data-raw '{
        "applicationName": "my-app",
        "repositoryUrl": "https://github.com/john/examplerepo",
        "revision": "HEAD",
        "path": "workflows"
    }'
```

-   `url`: URL of the git repository

-   `username`: \(Service\) user that is accessing the git repository

-   `password`: git personal access token. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


Since each application points to a particular path and revision in the repository, multiple applications may be created for the same `repositoryUrl`.



<a name="task_i3h_n13_tcc__result_psd_vjp_kyb"/>

## Results

After the GitOps setup is completed, the templates in your git repository are automatically synced to SAP AI Core approximately every three minutes.



<a name="task_i3h_n13_tcc__postreq_clx_ckp_kyb"/>

## Next Steps

Check the synchronization status of your application by submitting a GET request to `{{apiurl}}/v2/admin/applications/{{appName}}/status`:

```
curl --location --request GET "$AI_API_URL/v2/admin/applications/{{appName}}/status" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json'
```

As `applicationName`, enter the name of your application that you specified when you created the application.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__context_j2n_42b_wcc"/>

## Context

After you have registered your git repository, you need to create an application to sync the templates in your repository. The first sync takes some time, but you can check the status of the application to see when it is complete. After the first sync, syncing takes place automatically, every ~3 minutes, or can be requested manually.

-   `applicationName`: Set a name for your application. The name must be between 3 and 64 characters long and match `[A-Za-z0-9\-\_]+`.

-   `repositoryUrl`: The URL of a registered git repository.

-   `revision`: The revision to target. *<HEAD\>* refers to the most recent.

-   `path`: The path to the target folder that contains the templates to be synced.




<a name="task_cxf_n13_tcc__steps_k2n_42b_wcc"/>

## Procedure

Send a POST request to the endpoint `{{apiurl}}/v2/admin/applications` including details of your application:

-   `url`: URL of the git repository

-   `username`: \(Service\) user that is accessing the git repository

-   `password`: git personal access token. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


Since each application points to a particular path and revision in the repository, multiple applications may be created for the same `repositoryUrl`.



<a name="task_cxf_n13_tcc__result_psd_vjp_kxb"/>

## Results

After the GitOps setup is completed, the templates in your git repository are automatically synced to SAP AI Core approximately every three minutes.



<a name="task_cxf_n13_tcc__postreq_clx_ckp_kxb"/>

## Next Steps

Check the synchronization status of your application by sending a GET request to `{{apiurl}}/v2/admin/applications/{{appName}}/status`. As `applicationName`, enter the name of your application that you specified when you created the application.

> ### Output Code:  
> ```
> {
> 	"healthStatus": "Healthy",
> 	"message": "successfully synced (all tasks run)",
> 	"reconciledAt": "2021-11-23T10:27:49Z",
> 	"source": {
> 		"path": "workflows",
> 		"repoURL": "https://github.com/username/examplerepo",
> 		"revision": "db611bb28be3c853d08867c08b52b8f733b4f7bf",
> 	},
> 	"syncFinishedAt": "2021-11-23T10:27:49Z",
> 	"syncResourceStatus": [
> 		{
> 		"kind": "ServingTemaplate",
> 		"message": "servingtemplate.ai.sap.com/text-clf-infer-tutorial configured",
> 		"name": "text-clf-infer-tutorial",
> 		"status": "Synced",
> 		}
> 	],
> 	"syncedStartedAt": ""2021-11-23T10:27:48Z",",
> 	"syncStatus": "Synced",
> }
> ```

<a name="id_y5x_x2b_wcc"/>

<!-- id\_y5x\_x2b\_wcc -->

## Sync an Application Manually

Applications sync with your GitHub repository automatically at intervals of ~3 minutes. Use the endpoint below to manually request a sync:`{{apiurl}}/admin/applications/{{appName}}/refresh`

