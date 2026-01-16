<!-- loiobce96c1913e640e29a410bf0c8709849 -->

# Edit a Docker Registry Secret

Docker packages and runs applications in remote containers. Connect SAP AI Core to a Docker repository and manage access using a Docker registry secret.

<a name="task_i3h_n13_rtcc"/>

<!-- task\_i3h\_n13\_rtcc -->

## Using Curl



<a name="task_i3h_n13_rtcc__context_hk3z_jtf_mxb"/>

## Context

Your Docker credentials are managed using secrets. Secrets allow and control connections across directories and tools without compromising your credentials.

Your Docker registry secret lets you authorize SAP AI Core to pull your **private** Docker images from your Docker repository. You specify the name of the secret in your workflows to authenticate the Docker image pull. For more information, see [Workflow Templates](https://help.sap.com/viewer/db13d59d17204c01b3b79c24fb82a19a/CLOUD/en-US/83523ab8b49245bcbc9f1bf0969e32d8.html "Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.") :arrow_upper_right: and [Serving Templates](https://help.sap.com/viewer/db13d59d17204c01b3b79c24fb82a19a/CLOUD/en-US/20a8667ef19e4de59a4469cb542a7457.html "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.") :arrow_upper_right:.



<a name="task_i3h_n13_rtcc__steps_iwk3_jtf_mxb"/>

## Procedure

Submit a PATCH request to the endpoint `$AI_API_URL/v2/admin/dockerRegistrySecrets/{{dockerRegistryName}}`, Include the following parameters in your request body:

-   `name`: Set the name of your Docker registry secret.
-   `data`: Enter a JSON string that represents your Docker registry secret.

> ### Sample Code:  
> ```json
> {
> "name": "mydockerregistry",
> "data": {
> ".dockerconfigjson": "{\"auths\":{\"your.private.registry\":{\"username\":\"john\",\"password\":\"docker-accesstoken-or-password\"}}}"
> }
> }
> ```

> ### Note:  
> If you are using a public Docker registry from [http://hub.docker.com](http://hub.docker.com), you must provide your Docker URL in the format `https://index.docker.io`, in the *<\\"auths\\"\>* variable input.

```
$ curl --location --request PATCH "$AI_API_URL/v2/admin/dockerRegistrySecrets/{{dockerRegistryName}}" --header "Authorization: Bearer $TOKEN" --header 'Content-Type: application/json' --data-raw '{
	"name": "mydockerregistry",
	"data": {
		".dockerconfigjson": "{\"auths\": {\"my.docker.repositories.io\": {\"username\":\"$USERNAME\", \"password\": \"$PWD\"}}}"
	}
}

```

<a name="task_cxf_n13_itcc"/>

<!-- task\_cxf\_n13\_itcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_itcc__steps_sbr_n52_zcc"/>

## Procedure

Send a PATCH request to the endpoint `{{apiurl}}/v2/admin/repositories/{{repositoryName}}` and include your changes in the body.

You specify your unique git repository details as follows:

-   `url`: URL of the git repository

-   `username`: \(Service\) user that’s accessing the git repository

-   `password`: git personal access token. For more information, see [Create a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


> ### Tip:  
> To share a repository between two tenants, register the repository in SAP AI Core separately for each tenant and provide the **same** `username` and `password`.

