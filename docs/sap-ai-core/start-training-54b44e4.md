<!-- loio54b44e4099c3436db1c02242489435d8 -->

# Start Training

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



## Prerequisites

You know the configuration ID of the configuration that you want to start an execution for. For more information, see [List Configurations](list-configurations-8074b2a.md).



## Context

You can start training by creating an execution for your configuration.

When you view the status of your execution, the results include progress details that are normalized to N/100 format. For example: “3/5” is normalized to “3/100”. Completed executions always show “100/100”

> ### Note:  
> Pod-level progress is not granular: If an execution spawns 3 pods, progress will jump through: “0/100” → “1/100” → “2/100” → “3/100” → “100/100”.

Additionally, you can implement custom progress reporting in your workflow code by including an `ARGO_PROGRESS_FILE`. For more information, see [Argo Progress File](https://argo-workflows.readthedocs.io/en/latest/progress/).



<a name="task_i3h_n13_tcc__steps_y4z_hcq_tcc"/>

## Procedure

1.  Send a POST request to the endpoint:`$AI_API_URL/v2/lm/executions`. Include your configuration ID in your request.

    Make sure that you've set the following headers:


    <table>
    <tr>
    <th valign="top">

    Header
    
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
    
    Bearer $TOKEN
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    AI-Resource-Group
    
    </td>
    <td valign="top">
    
    The resource group used in the activation steps
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    $AI\_API\_URL
    
    </td>
    <td valign="top">
    
    The base URL of your SAP AI Core environment. You can set the URL as an environment variable.
    
    </td>
    </tr>
    </table>
    
    ```
    curl --location --request POST '$AI_API_URL/v2/lm/executions' \   
    	--header "Authorization: Bearer $TOKEN" \
    	--header "AI-Resource-Group: $RESOURCE_GROUP" \
    	--header "Content-Type: application/json" \
    	--data'{<configurationID>}'
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

2.  To check the status of the execution, send a GET request to the endpoint: `$AI_API_URL/v2/lm/executions/$EXECUTION_ID`. Include your execution ID in your request.

    ```
    curl --request GET $AI_API_URL/v2/lm/executions/$EXECUTION_ID \
        --header "Authorization: Bearer $TOKEN" \
        --header "AI-Resource-Group: $RESOURCE_GROUP"  
    ```

    > ### Restriction:  
    > The number of pods used by executions is limited at tenant level. A tenant is allowed to have at least 50 pods before the quota is enforced. If your tenant reaches this limit, your execution will be queued. You can raise a ticket to increase your quota.

    > ### Note:  
    > If the status is dead or pending, there might be errors in the execution. You can check the execution logs for more details, see [Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md).




## Results

The response includes details of your request, including IDs, status, timestamps and progress.

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



## Prerequisites

You know the configuration ID of the configuration that you want to start an execution for. For more information, see [List Configurations](list-configurations-8074b2a.md).



## Context

You can start training by creating an execution for your configuration.

When you view the status of your execution, the results include progress details that are normalized to N/100 format. For example: “3/5” is normalized to “3/100”. Completed executions always show “100/100”

> ### Note:  
> Pod-level progress is not granular: If an execution spawns 3 pods, progress will jump through: “0/100” → “1/100” → “2/100” → “3/100” → “100/100”.

Additionally, you can implement custom progress reporting in your workflow code by including an `ARGO_PROGRESS_FILE`. For more information, see [Argo Progress File](https://argo-workflows.readthedocs.io/en/latest/progress/).



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




## Results

The response includes details of your request, including IDs, status, timestamps and progress.

