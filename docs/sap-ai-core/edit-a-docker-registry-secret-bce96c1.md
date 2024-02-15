<!-- loiobce96c1913e640e29a410bf0c8709849 -->

# Edit a Docker Registry Secret

Docker packages and runs applications in remote containers. Connect SAP AI Core to a Docker repository and manage access using a Docker registry secret.

Your Docker credentials are managed using secrets. Secrets are allow and control connections across directories and tools, without compromising your credentials.

Your Docker registry secret lets you authorize SAP AI Core to pull your **private** Docker images from your Docker repository. You specify the name of the secret in your workflows to authenticate the Docker image pull. For more information, see [Workflow Templates](workflow-templates-83523ab.md) and [Serving Templates](serving-templates-20a8667.md).



<a name="loiobce96c1913e640e29a410bf0c8709849__section_lfb_34f_mvb"/>

## Using Postman

1.  Send a PATCH request to the endpoint `{{apiurl}}/v2/admin/dockerRegistrySecrets/{{dockerRegistryName}}`
2.  As the request body, select the *raw* radiobutton and enter the following:

    ```
    {
    "name": "mydockerregistry",
    "data": {
    ".dockerconfigjson": "{\"auths\":{\"your.private.registry\":{\"username\":\"john\",\"password\":\"docker-accesstoken-or-password\"}}}"
    }
    }
    ```

    -   `name`: Set the name of your Docker registry secret.
    -   `data`: Enter a JSON string that represents your Docker registry secret.

3.  Send the request:



<a name="loiobce96c1913e640e29a410bf0c8709849__section_nqm_hqf_mvb"/>

## Using curl

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

1.  Submit a PATCH request to the endpoint `$AI_API_URL/v2/admin/dockerRegistrySecrets/{{dockerRegistryName}}` and include the name of your Docker registry secret along with the credentials for your repository. For example

    > ### Sample Code:  
    > ```
    > $ curl --location --request PATCH "$AI_API_URL/v2/admin/dockerRegistrySecrets/{{dockerRegistryName}}" --header "Authorization: Bearer $TOKEN" --header 'Content-Type: application/json' --data-raw '{
    > 	"name": "mydockerregistry",
    > 	"data": {
    > 		".dockerconfigjson": "{\"auths\": {\"my.docker.repositories.io\": {\"username\":\"$USERNAME\", \"password\": \"$PWD\"}}}"
    > 	}
    > }
    > 
    > ```


