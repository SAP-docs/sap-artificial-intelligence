<!-- loio200810f61be6465ea79be0dc98615dd5 -->

# Manage mTLS Certificate Secrets



## Context

mTLS certificate secrets let your SAP AI Core workloads authenticate to external services using mutual TLS \(mTLS\). SAP AI Core automatically retrieves X.509 client certificates from the SAP BTP Certificate Service on your behalf, eliminating the need for manual certificate management. To establish mTLS connections, you mount this certificate in your executions or deployments.

> ### Restriction:  
> mTLS certificate secrets are managed via the API and are available through SAP AI Core only.

When you create an mTLS certificate secret, the following procedure occurs:

1.  SAP AI Core requests a client certificate from the SAP BTP Certificate Service.
2.  The certificate and private key are stored as a TLS secret in your resource group's namespace.
3.  The response returns the `subjectDN` \(subject Distinguished Name\) of the issued certificate.
4.  You configure trust for this subject DN on your external target service.
5.  Your workload mounts the secret as a volume and uses the certificate files for mTLS authentication.

The certificate's subject DN includes organizational fields set by the BTP Certificate Service \(such as `C=`, `O=`, `OU=`\) and a `CN=` \(common name\) field that you can customize.

> ### Note:  
> The certificate and private key content are never returned by the API. They're only accessible inside a workload container through a volume mount. The API returns only certificate metadata, such as subject DN, expiry, serial number, and common name.



## Establishing Trust on the Target Service

After creating the secret, you must configure the external target service to trust certificates matching the subject DN returned in the creation response.

> ### Note:  
> The exact steps depend on the target service.

To establish trust on the target service, you need to achieve the following:

-   Register the SAP Cloud Root CA \(or the specific intermediate CA\) as a trusted issuer.
-   Configure an access policy or trust rule that maps the certificate's subject DN pattern to the appropriate authorization level.

> ### Remember:  
> If you delete an mTLS certificate secret or stop using it, you should also remove the trust configuration from the external service. Certificates may remain valid until their original expiry date even after the secret is deleted. For more information, see [Delete an mTLS certificate secret](delete-an-mtls-certificate-secret-0268aba.md) and [Service Offboarding](service-offboarding-08303fe.md)



## Certificate Lifecycle and Rotation

mTLS certificates have a limited validity period. You can check the `expiresAt` field via the `GET` endpoint to see when the certificate expires. For more information, see [List mTLS Certificate Secrets](list-mtls-certificate-secrets-c346719.md).

> ### Caution:  
> You're responsible for monitoring certificate expiry and rotating secrets before they expire.
> 
> To rotate a certificate, send a `PATCH` request to the secret's endpoint. Rotation generates a new certificate and key with the same subject DN. The old certificate remains valid until its original expiry, ensuring a seamless transition with no downtime. For more information, see [Rotate an mTLS Certificate Secret](rotate-an-mtls-certificate-secret-e427cc3.md).



### Recommended Rotation Practices

The following best practices are recommended:

1.  Monitor the `expiresAt` field of your mTLS certificate secrets regularly.
2.  Rotate the secret well before the expiry date \(for example, 30 days in advance\).
3.  If your workload caches the certificate in memory: restart it after rotation to pick up the new certificate.

    If your workload reads the certificate from disk on each request: the updated files are propagated automatically.




### Scope and Limitations

-   mTLS certificate secrets are scoped to a single resource group. They don't support main-tenant scope, tenant-wide scope, or shared resource groups.
-   Each secret produces one certificate. If you need multiple certificates \(for example, for different external services\), create multiple secrets.
-   The `commonName` field is optional and limited to 64 characters. If omitted, the secret name is used.
-   Secret names must consist of lowercase alphanumeric characters, hyphens, or dots only, with a maximum length of 252 characters.

-   **[Create an mTLS Certificate Secret](create-an-mtls-certificate-secret-d3a4678.md "Create an mTLS certificate secret so that your workloads can make mutually
        authenticated TLS (mTLS) requests to external services.")**  
Create an mTLS certificate secret so that your workloads can make mutually authenticated TLS \(mTLS\) requests to external services.
-   **[Consume mTLS Certificate Secrets](consume-mtls-certificate-secrets-6845793.md "You can consume mTLS certificate secrets in your workloads to authenticate securely with
    external services that require mutual TLS.")**  
You can consume mTLS certificate secrets in your workloads to authenticate securely with external services that require mutual TLS.
-   **[List mTLS Certificate Secrets](list-mtls-certificate-secrets-c346719.md "")**  

-   **[Get Details of an mTLS Certificate Secret](get-details-of-an-mtls-certificate-secret-ec96ce1.md "")**  

-   **[Rotate an mTLS Certificate Secret](rotate-an-mtls-certificate-secret-e427cc3.md "")**  

-   **[Delete an mTLS certificate secret](delete-an-mtls-certificate-secret-0268aba.md "Delete an mTLS certificate secret and retrieve the certificate's subject DN so that
		you can revoke trust on external services.")**  
Delete an mTLS certificate secret and retrieve the certificate's subject DN so that you can revoke trust on external services.

**Related Information**  


[Create an mTLS Certificate Secret](create-an-mtls-certificate-secret-d3a4678.md "Create an mTLS certificate secret so that your workloads can make mutually authenticated TLS (mTLS) requests to external services.")

[List mTLS Certificate Secrets](list-mtls-certificate-secrets-c346719.md "")

[Rotate an mTLS Certificate Secret](rotate-an-mtls-certificate-secret-e427cc3.md "")

[Consume mTLS Certificate Secrets](consume-mtls-certificate-secrets-6845793.md "You can consume mTLS certificate secrets in your workloads to authenticate securely with external services that require mutual TLS.")

[Get Details of an mTLS Certificate Secret](get-details-of-an-mtls-certificate-secret-ec96ce1.md "")

[Delete an mTLS certificate secret](delete-an-mtls-certificate-secret-0268aba.md "Delete an mTLS certificate secret and retrieve the certificate's subject DN so that you can revoke trust on external services.")

