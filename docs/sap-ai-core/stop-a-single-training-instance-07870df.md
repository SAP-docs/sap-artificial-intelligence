<!-- loio07870dfc89fe4218baeda95e994936da -->

# Stop a Single Training Instance

You can stop a running execution by submitting a PATCH request to `$AI_API_URL/v2/lm/executions/$EXECUTION \`.

> ### Note:  
> Stop is only enabled if the status is running or pending.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_ptg_smv_tcc"/>

## Procedure

Run the following code:

```
curl --request PATCH $AI_API_URL/v2/lm/executions/$EXECUTION \ --header "Authorization: Bearer $TOKEN" --header "AI-Resource-Group: $RESOURCE_GROUP" --header "Content-Type: application/json"
    -d '{
    "targetStatus": "STOPPED"
    }'
                        
```

> ### Output Code:  
> ```json
> {
>     "id": "ee6769e4dc19c0fd",
>     "message": "Execution modification scheduled"
> }
>     
> ```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_c3l_wmv_tcc"/>

## Procedure

Send a PATCH request to endpoint `{{apiurl}}/v2/lm/executions/{{executionid}}` including the execution ID of the execution that you want to stop.

```
{
	"targetStatus": "STOPPED"
}
```



<a name="task_cxf_n13_tcc__result_amr_vdy_byb"/>

## Results

> ### Output Code:  
> ```
> {
> 	"id": "e8c53facc2bfb87a",
> 	"message": "Execution modification scheduled"
> }
> ```

