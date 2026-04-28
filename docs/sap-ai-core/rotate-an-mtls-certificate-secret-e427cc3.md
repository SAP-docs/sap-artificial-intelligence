<!-- loioe427cc3c2b8e4c0c92162fa07a335d34 -->

# Rotate an mTLS Certificate Secret

Rotate an mTLS certificate secret to obtain a new certificate with the same subject DN. The old certificate remains valid until its original expiry date.



## Prerequisites

You've created at least one mTLS Certificate Secret. For more information, see [Create an mTLS Certificate Secret](create-an-mtls-certificate-secret-d3a4678.md).



## Context

Certificate rotation generates a new certificate and private key for the secret while preserving the subject DN. Because the subject DN doesn't change, you don't need to update the trust configuration on your external target service.

After rotation, the secret is updated with the new certificate and key. Running workloads that have mounted the secret as a volume will see the new certificate files after a short propagation delay. If your workload reads the certificate at startup and keeps it in memory, you must restart the workload to pick up the rotated certificate.

> ### Restriction:  
> mTLS certificate secrets are managed via the API and are available through SAP AI Core only.

> ### Tip:  
> You can rotate a secret multiple times. Each rotation produces a new certificate with a unique serial number. The previous certificate isn't revoked and remains valid until its expiry date. This overlap allows you to rotate without downtime.



## Procedure

Send a PATCH request to the endpoint `$AI_API_URL/v2/admin/mtlsCertificateSecrets`.

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl --location --request PATCH "$AI_API_URL/v2/admin/mtlsCertificateSecrets" \
> --header "Authorization: Bearer $TOKEN" \
> --header 'AI-Resource-Group: default'
> 
> ```



## Results

> ### Output Code:  
> ```
> 200 OK
> {
>     "name": "my-mtls-cert",
>     "message": "...",
>     "subjectDN": "C=DE, O=SAP SE, OU=SAP Cloud Platform Clients, OU=<subaccount-ou>, L=<locality-hash>, CN=my-service-client"
> }
> 
> ```

The `subjectDN` remains unchanged. You can verify the rotation by calling the `GET` endpoint and checking that `serialNumber` has changed and `expiresAt` has been extended. For more information, see [Get Details of an mTLS Certificate Secret](get-details-of-an-mtls-certificate-secret-ec96ce1.md).

