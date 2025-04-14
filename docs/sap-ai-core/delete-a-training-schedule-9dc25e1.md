<!-- loio9dc25e11c3b64fc59621082679f0e01f -->

# Delete a Training Schedule

You can delete training schedules that are in states ACTIVE and INACTIVE.

**Parent topic:**[Training Schedules](training-schedules-2b702f8.md "")

**Related Information**  


[Create a Training Schedule](create-a-training-schedule-bd409a9.md "")

[List Executions Created by a Training Schedule](list-executions-created-by-a-training-schedule-2c1ecfb.md "")

[Change an Existing Training Schedule](change-an-existing-training-schedule-18caf4b.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__context_egp_gpx_tcc"/>

## Context



<a name="task_i3h_n13_tcc__steps_fgp_gpx_tcc"/>

## Procedure

Submit a DELETE request:

```
curl --location -- request DELETE “$AI_API_URL/v2/lm/executionSchedules/$EXECUTION_SCHEDULE” \\
--header “Authorization: Bearer $TOKEN” \
--header “ai-resource-group: $RESOURCE_GROUP”
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__context_yhr_wpx_tcc"/>

## Context



<a name="task_cxf_n13_tcc__steps_zhr_wpx_tcc"/>

## Procedure

Send a DELETE request to the endpoint `{{apiurl}}/v2/lm/executionSchedules/{{executionScheduleId}}`

 > ### Output Code:  
> ```
> {
> 	"id": "799b4e67-a213-40b9-9550-637fde75dbda",
> 	"message": "Execution Schedule deleted"
> }
> ```

 