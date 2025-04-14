<!-- loioedf9b1b0d47c4db69a5bfb56f290c711 -->

# Delete Files

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_us3_fv3_tcc"/>

## Procedure

Run the following code:

```
curl --location --request DELETE “$AI_API_URL/v2/lm/dataset/files/$SECRET_NAME/$FILE_PATH” \\
	--header “Authorization: Bearer $TOKEN” \
	--header “ai-resource-group: $RESOURCE_GROUP
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_pyt_3v3_tcc"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/lm/dataset/files/{secret name}/{full file path}`

Ensure that the following headers are selected:

****


<table>
<tr>
<th valign="top">

Key

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

\{\{resource-group\}\}

</td>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

\{\{token\}\}

</td>
</tr>
</table>

