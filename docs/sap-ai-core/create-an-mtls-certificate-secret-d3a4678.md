<!-- loiod3a467832f8f40439dc62323bb919270 -->

# Create an mTLS Certificate Secret

Create an mTLS certificate secret so that your workloads can make mutually authenticated TLS \(mTLS\) requests to external services.



## Prerequisites

Make sure that you completed the initial setup. For more information, see [Initial Setup](initial-setup-38c4599.md).



## Context

An `mTLS` certificate secret instructs SAP AI Core to obtain an X.509 client certificate from the SAP BTP Certificate Service on your behalf. Unlike generic secrets, where you provide the credential payload, SAP AI Core generates both the certificate and the private key.

You can mount the generated certificate in executions or deployments to enable mTLS-authenticated requests to external services that trust the certificate's subject DN.

`mTLS` certificate secrets are scoped to a single resource group. They do not support main-tenant scope, tenant-wide scope, or shared resource groups.

When you create the secret, the response includes the `subjectDN`. You must configure trust for this subject DN on the external service before authentication succeeds.

You can optionally specify a `commonName`. If you omit it, SAP AI Core uses the secret name as the common name. The common name appears in the Common Name field of the certificate’s subject distinguished name.

> ### Note:  
> Creation is asynchronous. After you send a successful `POST` request \(HTTP 202\), the certificate may take a few moments to become available. Use a `GET` request to verify readiness before you run an execution or deployment that mounts the secret.



## Procedure

1.  Send a POST request to the endpoint <code><code>$AI_API_URL/v2/admin/mtlsCertificateSecrets</code> </code>.

2.  Include the `AI-Resource-Group` header to specify the resource group.

    **Minimal request \(common name defaults to secret name\):**

    ```
    curl --location --request POST "$AI_API_URL/v2/admin/mtlsCertificateSecrets" \
    --header "Authorization: Bearer $TOKEN" \
    --header "Content-Type: application/json" \
    --header "AI-Resource-Group: default" \
    --data-raw '{
        "name": "my-mtls-cert"
    }'
    ```

    **Request with a custom common name:**

    ```
    curl --location --request POST "$AI_API_URL/v2/admin/mtlsCertificateSecrets" \
    --header "Authorization: Bearer $TOKEN" \
    --header "Content-Type: application/json" \
    --header "AI-Resource-Group: default" \
    --data-raw '{
        "name": "my-mtls-cert",
        "data": {
            "commonName": "my-service-client"
        }
    }'
    ```

    > ### Note:  
    > The secret name must match the pattern `^[a-z0-9\-\.]+$` and be at most 252 characters. A common name can be up to 64 characters.




## Results

The service returns HTTP `202 Accepted` and includes the issued certificate’s subject DN.

> ### Output Code:  
> ```
> 202 Accepted
> {
>     "name": "my-mtls-cert",
>     "message": "...",
>     "subjectDN": "C=DE, O=SAP SE, OU=SAP Cloud Platform Clients, OU=<subaccount-ou>, L=<locality-hash>, CN=my-service-client"
> }
> ```

Use the returned `subjectDN` to configure trust on the external service.

<a name="task_cl5_cjc_q3c"/>

<!-- task\_cl5\_cjc\_q3c -->

## Using a Third-Party API Platform



## Procedure

1.  Send a POST request to `{{apiurl}}/v2/admin/mtlsCertificateSecrets.`

2.  Select *raw* for the request body and enter the JSON payload.

    ```
    
    {
        "name": "my-mtls-cert",
        "data": {
            "commonName": "my-service-client"
        }
    }
                            
    ```

3.  Set the `AI-Resource-Group` header to the target resource group name.

4.  Send the request.


