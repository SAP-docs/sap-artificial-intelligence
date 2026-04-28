<!-- loioec96ce1cef294d3bab728b1d785a8948 -->

# Get Details of an mTLS Certificate Secret

Retrieve metadata for a single mTLS certificate secret. The response includes certificate metadata such as the subject DN, expiry date, and serial number. The actual certificate and private key are never returned by the API; they are only accessible by mounting the secret in an execution or deployment.



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

The response contains certificate metadata. No sensitive information is revealed.

> ### Output Code:  
> ```
> 200 OK
> {
>     "name": "my-mtls-cert",
>     "createdAt": "2024-07-01T12:00:00Z",
>     "subjectDN": "C=DE, O=SAP SE, OU=SAP Cloud Platform Clients, OU=<subaccount-ou>, L=<locality-hash>, CN=my-service-client",
>     "locality": "<locality-hash>",
>     "commonName": "my-service-client",
>     "expiresAt": "2024-10-01T12:00:00Z",
>     "serialNumber": "aabbccdd..."
> }
> 
> ```

