<!-- loio18caf4b12bbe474a85626cec00de4455 -->

# Change an Existing Training Schedule

You can change the cron definition, start, end, and configuration of an existing training schedule.

You cannot change the name field.

**Parent topic:**[Training Schedules](training-schedules-2b702f8.md "")

**Related Information**  


[Create a Training Schedule](create-a-training-schedule-bd409a9.md "")

[List Executions Created by a Training Schedule](list-executions-created-by-a-training-schedule-2c1ecfb.md "")

[Delete a Training Schedule](delete-a-training-schedule-9dc25e1.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_tvj_rnp_yxb"/>

## Procedure

Submit a PATCH request:

```
curl --location --request PATCH $AI_API_URL/v2/lm/executions?executionScheduleId=$EXECUTION_SCHEDULE
--header “Authorization: Bearer $TOKEN” \
--header “ai-resource-group: $RESOURCE_GROUP” \
--data-raw '{ "cron": "0 0 * * *"
}'
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using Postman



<a name="task_cxf_n13_tcc__steps_zvd_cqx_tcc"/>

## Procedure

Send your changes in a PATCH request to `{{apiurl}}/v2/lm/executionSchedules/{{executionScheduleId}}`.

```
{
	"cron": "0 * * * * *",
}
```

> ### Output Code:  
> ```
> {
> 	"id": "799b4e67-a213-40b9-9550-637fde75dbda",
> 	"message": "Execution Schedule modified"
> }
> ```

<a name="id_msy_jqx_tcc"/>

<!-- id\_msy\_jqx\_tcc -->

## Pause or Resume a Training Schedule



The `status` parameter pauses or resumes a schedule:

-   *<INACTIVE\>*: pauses a schedule.
-   *<ACTIVE\>*: resumes a schedule.

