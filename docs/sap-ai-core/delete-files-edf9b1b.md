<!-- loioedf9b1b0d47c4db69a5bfb56f290c711 -->

# Delete Files



<a name="loioedf9b1b0d47c4db69a5bfb56f290c711__section_uk3_jds_2xb"/>

## Using Postman

Send a DELETE request to the endpoint `{{apiurl}}/v2/lm/dataset/files/{secret name}/{full file path}`

![](images/Delete_Postman_be27b83.png)



<a name="loioedf9b1b0d47c4db69a5bfb56f290c711__section_dw3_kds_2xb"/>

## Using Curl

```
curl --location --request DELETE “$AI_API_URL/v2/lm/dataset/files/$SECRET_NAME/$FILE_PATH” \\
	--header “Authorization: Bearer $TOKEN” \
	--header “ai-resource-group: $RESOURCE_GROUP
```

