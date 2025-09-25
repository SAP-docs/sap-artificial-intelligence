<!-- loiodd71f165135f49a194e131fa4ca9d5d3 -->

# Delete a Single Training Instance

Deleting a training instance releases the SAP AI Core resources that it used.

> ### Restriction:  
> If your execution is running, you must stop it first.You can stop a running execution by submitting a PATCH request to `$AI_API_URL/v2/lm/executions/$EXECUTION \`. For more information, see [Stop a Single Training Instance](stop-a-single-training-instance-07870df.md) and [Stop Multiple Training Instances](stop-multiple-training-instances-09b4810.md).

**Parent topic:**[Delete Training Instances](delete-training-instances-612ce17.md "")

**Related Information**  


[Delete Multiple Training Instances](delete-multiple-training-instances-c1c3cc3.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_odm_hyv_tcc"/>

## Procedure

Run the following code:

```
curl --request DELETE $AI_API_URL/v2/lm/executions/$EXECUTION \ \
							--header "Authorization: Bearer $TOKEN" \
							--header "AI-Resource-Group: $RESOURCE_GROUP"  
							
						
```

> ### Output Code:  
> ```json
> {
> 								"id": "ee6769e4dc19c0fd",
> 								"message": "Deletion scheduled",
> 								"targetStatus": "DELETED"
> 								}
> 							
> ```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_dvh_b4w_tcc"/>

## Procedure

Send a DELETE request to `{{apiurl}}/v2/lm/executions/{{executionid}}`. The header for this request is: `AI-Resource-Group: {YOUR-Resource-Group}`.

```
{
	"targetStatus": "DELETED"
}
```



<a name="task_cxf_n13_tcc__result_amr_vdy_byb"/>

## Results

> ### Output Code:  
> ```
> {
> 	"id": "e8c53facc2bfb87a",
> 	"message": "Deletion scheduled",
> 	"targetStatus": "DELETED"
> }
> ```

