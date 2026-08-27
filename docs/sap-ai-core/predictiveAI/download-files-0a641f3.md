<!-- loio0a641f3e5e35421ba9ebdbf43b68decc -->

# Download Files

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_crf_553_tcc"/>

## Procedure

Run the following code:

```
curl --location --request GET “$AI_API_URL/v2/lm/dataset/files/$SECRET_NAME/$FILE_PATH” \\
	--header “Authorization: Bearer $TOKEN” \
	--header “AI-Resource-Group: $RESOURCE_GROUP” \
	--data @$FILE_LOCATION
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_gfw_y53_tcc"/>

## Procedure

Send a GET request to the endpoint `{{apiurl}}/v2/lm/dataset/files/{secret name}/{full file path}`

