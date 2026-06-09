<!-- loio04664599dc4545b19581f64dd6242186 -->

# Create Files

Where direct access to files in the object store is not possible or desirable \(for example, in Content as a Service Scenarios, where the Service Consumers might not be the owners of the object store\) you can upload, download, and delete files from the pre-registered object store using the SAP AI Core Dataset API.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__prereq_ry1_pgw_txb"/>

## Prerequisites

-   You must have an object store secret defined in the target resource group.

> ### Restriction:  
> Only S3 object stores can be used with the Dataset API.

> ### Restriction:  
> Only `csv` type files can be uploaded with the Dataset API.



<a name="task_i3h_n13_tcc__context_jl3_f53_tcc"/>

## Context

For full details on the Dataset API specification, see [SAP AI Core Dataset API documentation](https://api.sap.com/api/AI_CORE_API/resource/File).



<a name="task_i3h_n13_tcc__steps_kmf_rt3_tcc"/>

## Procedure

Run the following code:

```
curl --location --request PUT “$AI_API_URL/v2/lm/dataset/files/$SECRET_NAME/$FILE_PATH” \\
	--header “Authorization: Bearer $TOKEN” \
	--header “Content-Type: text/csv” \
	--header “AI-Resource-Group: $RESOURCE_GROUP” \
	--data @$FILE_LOCATION
```

-   If you use a service provider token, specify the resource group.

    If you use a service consumer token, the resource group information is contained in the token, and need not be specified.

-   In the request body, submit the file as binary data.


<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__prereq_zzz_f53_tcc"/>

## Prerequisites

-   You must have an object store secret defined in the target resource group.

> ### Restriction:  
> Only S3 object stores can be used with the Dataset API.

> ### Restriction:  
> Only `csv` type files can be uploaded with the Dataset API.



<a name="task_cxf_n13_tcc__context_tpz_f53_tcc"/>

## Context

For full details on the Dataset API specification, see [SAP AI Core Dataset API documentation](https://api.sap.com/api/AI_CORE_API/resource/File).



<a name="task_cxf_n13_tcc__steps_t5z_q53_tcc"/>

## Procedure

1.  Send a PUT request to the endpoint `{{apiurl}}/v2/lm/dataset/files/{secret name}/{full file path}`

2.  In the header set the `Content-Type` as *<text/csv\>*.

3.  If you use a service provider token, specify the resource group. If you use a service consumer token, the resource group information is contained in the token, and need not be specified.

4.  In the request body, submit the file as binary data.




<a name="task_cxf_n13_tcc__result_dlf_2ld_5xb"/>

## Results

Your file will be uploaded to the S3 storage bucket with the prefix specified in the object store secret, and the full file path specified in the upload request.

> ### Output Code:  
> ```
> {
> "message": "File default/test.csv created successfully.",
> "url": "ai://default/test.csv"
> }
> ```

