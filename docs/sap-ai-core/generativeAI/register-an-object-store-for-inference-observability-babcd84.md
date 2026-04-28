<!-- loiobabcd844f6164c628469910bba9d36bf -->

# Register an Object Store for Inference Observability

Connect SAP AI Core to a cloud object store and manage access using an object store secret. The connected storage stores your dataset, models, and other cache files of the Metaflow Library for.



## Context

Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.

To store the inference request, response, and feedback, you'll need an object store that has been registered using an object store secret.

> ### Restriction:  
> Only S3 object stores are supported by inference observability.

> ### Caution:  
> You're responsible for the rotation of your access credentials and certificates of SAP AI Core within BTP according to regional policy.



## Procedure



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

Register the details of your object store secret using the endpoint `/v2/admin/objectStoreSecrets`. All *<data\>* fields are required.

> ### Sample Code:  
> ```
> curl --location --request POST "$AI_API/admin/objectStoreSecrets" \
> --header "Authorization: Bearer {{access_token}}" \
> --header 'Content-Type: application/json' \
> --header 'AI-Resource-Group: {{resource-group}}' \
> --data-raw '{
>   "name": "default",
>   "type": "S3",
>   "bucket": "<S3 bucket name>",
>   "endpoint": "<S3 end point>",
>   "pathPrefix": "<A path prefix that follows the bucket name>",
>   "region": "<S3 region>",
>   "data": {
>     "AWS_ACCESS_KEY_ID": "<AWS access key ID>",
>     "AWS_SECRET_ACCESS_KEY": "<AWS secret access key>"
>   }
> }'
> ```



## Results

Successful responses return code **202** and include a success message.

