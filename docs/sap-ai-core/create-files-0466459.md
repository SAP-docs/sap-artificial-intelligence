<!-- loio04664599dc4545b19581f64dd6242186 -->

# Create Files



<a name="loio04664599dc4545b19581f64dd6242186__section_bqr_gds_2xb"/>

## Using Postman

1.  Send a PUT request to the endpoint `{{apiurl}}/v2/lm/dataset/files/{secret name}/{full file path}`
2.  In the header set the `Content-Type` as *<text/csv\>*.
3.  If you use a service provider token, specify the resource group.

    If you use a service consumer token, the resource group information is contained in the token, and need not be specified.

4.  In the request body, submit the file as binary data.




### Results

Your file will be uploaded to the S3 storage bucket with the prefix specified in the object store secret, and the full file path specified in the upload request.



<a name="loio04664599dc4545b19581f64dd6242186__section_arf_dds_2xb"/>

## Using curl

```
curl --location --request PUT “$AI_API_URL/v2/lm/dataset/files/$SECRET_NAME/$FILE_PATH” \\
	--header “Authorization: Bearer $TOKEN” \
	--header “Content-Type: text/csv” \
	--header “ai-resource-group: $RESOURCE_GROUP” \
	--data @$FILE_LOCATION
```

-   If you use a service provider token, specify the resource group.

    If you use a service consumer token, the resource group information is contained in the token, and need not be specified.

-   In the request body, submit the file as binary data.




### Results

Your file will be uploaded to the S3 storage bucket with the prefix specified in the object store secret, and the full file path specified in the upload request.

