<!-- loio0268aba45929405a960beca2739ad93f -->

# Delete an mTLS certificate secret

Delete an mTLS certificate secret and retrieve the certificate's subject DN so that you can revoke trust on external services.



## Prerequisites

To get the secret name, see [List mTLS Certificate Secrets](list-mtls-certificate-secrets-c346719.md).



## Context

You've completed the initial setup. For more information, see [Initial Setup](initial-setup-38c4599.md).

When you delete an mTLS certificate secret, the response includes the `subjectDN` of the certificate. Use this subject DN to revoke trust on the external service where you previously configured it.

If you do not revoke trust, any unexpired certificate issued for the same subject DN \(for example, a certificate from before rotation\) may still authenticate successfully.



## Procedure

1.  Send a DELETE request to the endpoint <code><code>$AI_API_URL/v2/admin/mtlsCertificateSecrets/$SECRET_NAME</code> </code>.

2.  Include the `AI-Resource-Group` header to specify the resource group.

3.  Run the following request:

    ```
    
    curl --location --request DELETE "$AI_API_URL/v2/admin/mtlsCertificateSecrets/$SECRET_NAME" \
    --header "Authorization: Bearer $TOKEN" \
    --header "AI-Resource-Group: default"
                    
    ```




## Results

The service returns HTTP **200 OK** and the subject DN of the deleted certificate.

```

200 OK
{
    "name": "my-mtls-cert",
    "message": "...",
    "subjectDN": "C=DE, O=SAP SE, OU=SAP Cloud Platform Clients, OU=<subaccount-ou>, L=<locality-hash>, CN=my-service-client"
}
        
```

> ### Note:  
> After deleting the secret, remove the trust configuration from your external service. The certificate may remain valid until its original expiry date even though the secret has been deleted from SAP AI Core.

<a name="task_tx3_klc_q3c"/>

<!-- task\_tx3\_klc\_q3c -->

## Get a Secret Using a Third-Party API Platform



## Procedure

1.  Send a GET request to the endpoint `$AI_API_URL/v2/admin/mtlsCertificateSecrets/$SECRET_NAME`.

2.  As the request body, select the \*none\* radio button.

3.  Set the header \`AI-Resource-Group\` to the name of the resource group.

4.  Send the request.




## Results

> ### Output Code:  
> ```
> 200 OK
> {
>     "name": "my-mtls-cert",
>     "message": "...",
>     "subjectDN": "..."
> }
>         
> ```

