<!-- loioc3467196e3b14f3381c242ed1261f32e -->

# List mTLS Certificate Secrets

Retrieve a list of mTLS certificate secrets in a resource group. The response includes certificate metadata such as the subject DN, expiry date, and serial number. The actual certificate and private key are never returned by the API; they are only accessible by mounting the secret in an execution or deployment.



## Prerequisites

You've created at least one mTLS Certificate Secret. For more information, see [Create an mTLS Certificate Secret](create-an-mtls-certificate-secret-d3a4678.md).



## Procedure

Submit a GET request to the endpoint `$AI_API_URL/v2/admin/mtlsCertificateSecrets`:

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
> curl --location --request GET "$AI_API_URL/v2/admin/mtlsCertificateSecrets" \
> --header "Authorization: Bearer $TOKEN" \
> --header 'AI-Resource-Group: default'
> 
> ```



## Results

The response contains a list of mTLS certificate secret metadata objects.

> ### Output Code:  
> ```
> 200 OK
> {
>     "count": 2,
>     "resources": [
>         {
>             "name": "my-mtls-cert",
>             "createdAt": "2026-03-01T12:00:00Z",
>             "subjectDN": "...",
>             "locality": "<locality-hash>",
>             "commonName": "my-service-client",
>             "expiresAt": "2024-10-01T12:00:00Z",
>             "serialNumber": "aabbccdd..."
>         },
>         {
>             "name": "another-cert",
>             "createdAt": "2026-03-02T12:00:00Z",
>             "subjectDN": "...",
>             "locality": "<locality-hash>",
>             "commonName": "another-cert",
>             "expiresAt": "2024-10-02T12:00:00Z",
>             "serialNumber": "eeff0011..."
>         }
>     ]
> }
> 
> ```

