<!-- loiod5d5187da4d2483baa6a203f1bcbe33a -->

# Delete a Generic Secret

To get a secret name, see [List All Generic Secrets](list-all-generic-secrets-05a3713.md).



<a name="loiod5d5187da4d2483baa6a203f1bcbe33a__section_xnr_myk_4rb"/>

## Using Postman

1.  Send a DELETE request to the endpoint***\{\{apiurl\}\}/v2/admin/secrets/\{\{secretName\}\}***
2.  As the request body, select the *none* radiobutton.
3.  Specify the scope of the request via the header `AI-Tenant-Scope` or `AI-Resource-Group`:
    -   ***AI-Tenant-Scope*** : ***true***. The operation will be performed at the main tenant level.
    -   ***AI-Resource-Group*** : ****<resource-group-name\>****. The operation will be performed at the resource-group level.

4.  Send the request.

 ![](images/Delete_Generic_Secrets_in_Postman_798b308.png)



<a name="loiod5d5187da4d2483baa6a203f1bcbe33a__section_y24_pyk_4rb"/>

## Using curl

Submit a DELETE request to the endpoint `/v2/admin/secrets/"$SECRET_NAME"`. Here we use the resource-group scope. For main-tenant scope level, replace the last header with `AI-Tenant-Scope: true`.

```
curl --location --request DELETE "$AI_API_URL/v2/admin/secrets/$SECRET_NAME$AI_API_URL/v2/admin/secrets/$SECRET_NAME" \
--header "Authorization: Bearer $TOKEN" \
--header 'AI-Resource-Group: default' 

```

