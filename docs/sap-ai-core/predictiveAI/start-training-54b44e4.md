<!-- loio54b44e4099c3436db1c02242489435d8 -->

# Start Training

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_y4z_hcq_tcc"/>

## Procedure

1.  Run the following code:

    ```
    curl --location --request POST '$AI_API_URL/v2/lm/executions' \
    ```

    > ### Output Code:  
    > ```json
    > {
    >   "id": "dea6263e6283321b",
    >   "message": "Execution scheduled",
    >   "status": "UNKNOWN",
    >   "targetStatus": "COMPLETED"
    > }
    > ```

2.  Check the status of the execution.

    ```
    curl --request GET $AI_API_URL/v2/lm/executions/$EXECUTION \ \
        --header "Authorization: Bearer $TOKEN" \
        --header "AI-Resource-Group: $RESOURCE_GROUP"  
    ```

    > ### Restriction:  
    > The number of pods used by executions is limited at tenant level. A tenant is allowed to have at least 50 pods before the quota is enforced. If your tenant reaches this limit, your execution will be queued. You can raise a ticket to increase your quota.

    > ### Note:  
    > If the status is dead or pending, there might be errors in the execution. You can check the execution logs for more details, see [Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md).


<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_ucc_4cq_tcc"/>

## Procedure

1.  Send a POST request to the endpoint `{{apiurl}}/v2/lm/executions`. Pass the `configurationId` in the request body.

    ```
    {
    "configurationId": "47b3eed9-f72f-4a18-b2ab-25b057a3e77f"
    }
    ```

2.  Check the status of the execution by submitting a GET request to `{{apiurl}}/v2/lm/executions/{{executionid}}`.

    Check that the following headers are selected:

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
    
    Authorization
    
    </td>
    <td valign="top">
    
    \{\{token\}\}
    
    </td>
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
    
    Content-Type
    
    </td>
    <td valign="top">
    
    application/json
    
    </td>
    </tr>
    </table>
    
    > ### Restriction:  
    > The number of pods used by executions is limited at tenant level. A tenant is allowed to have at least 50 pods before the quota is enforced. If your tenant reaches this limit, your execution will be queued. You can raise a ticket to increase your quota.

    > ### Note:  
    > If the status is dead or pending, there might be errors in the execution. You can check the execution logs for more details, see [Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md).


