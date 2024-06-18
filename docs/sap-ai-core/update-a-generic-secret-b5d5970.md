<!-- loiob5d597051e494b49a4907470f1b238af -->

# Update a Generic Secret

To update a generic secret, use the PATCH endpoint as shown below. The PATCH operation replaces the secret with the data provided. This can be used for rotating secret credentials.



<a name="loiob5d597051e494b49a4907470f1b238af__section_ehc_cyk_4rb"/>

## Using Postman

1.  Send a PATCH request to the endpoint `{{apiurl}}/v2/admin/secrets/{{secretName}}`
2.  As the request body, select the *raw* radio button and enter the following code:

    > ### Source Code:  
    > ```
    > {
    > 	"data": {
    > 		"updated-credentials": "bXktc2VjcmV0LW90aGVyLWNyZWRlbnRpYWw="
    > 	}
    > } and specify the scope via the
    > 					
    > ```

3.  Specify the scope of the request via the header `AI-Tenant-Scope` and specify the scope via the or `AI-Resource-Group`:
    -   `AI-Tenant-Scope` : `true`. The operation will be performed at the main tenant level.
    -   `AI-Resource-Group` : <code><i class="varname">&lt;resource-group-name&gt;</i></code>. The operation will be performed at the resource-group level.

4.  Send the request.

![](images/Update_Generic_Secrets_in_Postman_414a8c7.png)



<a name="loiob5d597051e494b49a4907470f1b238af__section_wgc_2yk_4rb"/>

## Using curl

Submit a PATCH request to the endpoint `/v2/admin/secrets/"$SECRET_NAME"``AI-Tenant-Scope` or `AI-Resource-Group` header.

```
curl --location --request PATCH "$AI_API_URL/v2/admin/secrets/$SECRET_NAME" \
--header "Authorization: Bearer $TOKEN" \
--header 'Content-Type: application/json' \
--header 'AI-Resource-Group: default' \
--data-raw '{
		"data": {
			"some-credential": "bXktc2Vuc2l0aXZlLWRhdGE="
			}
}'
```

