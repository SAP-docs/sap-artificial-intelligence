<!-- loioa7cf5e1496eb4ea8beca79671f49ff66 -->

# Register Your Docker Registry Secret

Your Docker credentials are managed using secrets. Secrets are allow and control connections across directories and tools, without compromising your credentials.



<a name="loioa7cf5e1496eb4ea8beca79671f49ff66__section_jnm_xnf_mvb"/>

## Context

Your Docker registry secret lets you authorize SAP AI Core to pull your **private** Docker images from your Docker repository. You specify the name of the secret in your workflows to authenticate the Docker image pull. For more information, see [Workflow Templates](workflow-templates-83523ab.md) and [Serving Templates](serving-templates-20a8667.md).



<a name="loioa7cf5e1496eb4ea8beca79671f49ff66__section_lfb_34f_mvb"/>

## Using Postman

1.  Open the AI-API collection and create a new POST request with the URL `{{apiurl}}/v2/admin/dockerRegistrySecrets`
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

     ![](images/Register_Docker_Registry_Secret_with_Postman_7eccfad.png) 

4.  After your Docker registry secret has been created, reference it in your template as an image pull secret.

    > ### Source Code:  
    > ```
    > spec:
    >     imagePullSecrets:
    >     - name: <Name of your Docker registry secret>
    > ```




<a name="loioa7cf5e1496eb4ea8beca79671f49ff66__section_nqm_hqf_mvb"/>

## Using curl

You configure your Docker registry by submitting a call to the `{{apiurl}}/v2/admin/dockerRegistrySecrets` endpoint. Include the following parameters in your request body:

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

1.  Submit a POST request to the endpoint `{{apiurl}}/v2/admin/dockerRegistrySecrets` and include the name of your Docker registry secret along with the credentials for your repository. For example

    > ### Sample Code:  
    > ```
    > $ curl --location --request POST "[/pandoc/div/div/horizontalrule/orderedlist/li/note/codeblock/span/code
    >      {"filepath"}) $AI_API_URL/v2/admin/dockerRegistrySecrets (code]" --header "Authorization: Bearer $TOKEN" --header 'Content-Type: application/json' --data-raw '{
    > 	"name": "mydockerregistry",
    > 	"data": {
    > 		".dockerconfigjson": "{\"auths\": {\"my.docker.repositories.io\": {\"username\":\"$USERNAME\", \"password\": \"$PWD\"}}}"
    > 	}
    > }
    > {
    > 	"message": "secret has been created"
    > }
    > ```

2.  After your Docker registry secret has been created, reference it in your template as an image pull secret. For example

    > ### Source Code:  
    > ```
    > spec:
    >     imagePullSecrets:
    >     - name: <Name of your Docker registry secret>
    > ```


**Parent topic:** [Manage Docker Registry Secrets](manage-docker-registry-secrets-c5445c4.md "Docker facilitates the packaging and running of an application in a remote container. Connect SAP AI Core to a Docker repository and manage access using a Docker registry secret.")

