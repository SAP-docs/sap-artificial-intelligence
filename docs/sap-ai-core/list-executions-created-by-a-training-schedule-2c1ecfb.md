<!-- loio2c1ecfb94988479b95d6a7bfd2784e2e -->

# List Executions Created by a Training Schedule

**Parent topic:**[Training Schedules](training-schedules-2b702f8.md "")

**Related Information**  


[Create a Training Schedule](create-a-training-schedule-bd409a9.md "")

[Change an Existing Training Schedule](change-an-existing-training-schedule-18caf4b.md "")

[Delete a Training Schedule](delete-a-training-schedule-9dc25e1.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_k55_wfx_tcc"/>

## Procedure

Run the following code:

```
curl --location -- request GET “$AI_API_URL/v2/lm/executionSchedules/$EXECUTION_SCHEDULE” \\
--header “Authorization: Bearer $TOKEN” \
--header “ai-resource-group: $RESOURCE_GROUP”
```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_vjx_tpx_tcc"/>

## Procedure

Get a list of executions created by a training schedule by submitting a GET request to `{{apiurl}}/v2/lm/executions?executionScheduleId={{executionScheduleId}}`

> ### Output Code:  
> ```
> "count": 2,
> 	"resources": [
> 	{
> 		"completionTime": "2023-02-08T12:02:56Z",
> 		"configurationId": "36b60691-1e48-473b-9b44-d6f8e9r4de32"
> 		"configurationName": "test-for-demo",
> 		"createdAt": "2023-02-08T12:56:31Z",
> 		"executionId": "9aea6ade-747d-42eb-ba7c-7dcb617e955a",
> 		"id": "ef7877dffb8394be",
> 		"modifiedAt": "2023-02-08T12:02:48Z",
> 		"outputArtifacts": [],
> 		"scenarioId": "platform-test-tensorflow",
> 		"startTime": "2023-02-08T12:02:48Z",
> 		"targetStatus": "COMPLETED"		
> };
> ...
> ```

