<!-- loio9ddbaab65e1c40b1a4e62bde2312c3b0 -->

# Create an Execution for your Optimization



## Prerequisites

You've created a configuration for your optimization. For more information, see [Create a Configuration for an Optimization](create-a-configuration-for-an-optimization-40ba168.md).



## Procedure

To create an execution, send a POST request to endpoint `$AI_API_URL/v2/lm/executions`. Include your configuration ID in your request.


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
<tr>
<td valign="top">

$RESOURCE\_GROUP

</td>
<td valign="top">

The AI resource group assigned to your account

</td>
</tr>
<tr>
<td valign="top">

$TOKEN

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

`configurationId` 

</td>
<td valign="top">

Your `configurationId` from the previous step

</td>
</tr>
</table>

For example:

> ### Sample Code:  
> ```
> curl --request POST "$AI_API_URL/v2/lm/executions"
> --header "Authorization: Bearer $TOKEN"
> --header "AI-Resource-Group: $RESOURCE_GROUP"
> --header "Content-Type: application/json" \
> --data '{"configurationId": "<YourConfigurationId>"}'
> ```



## Results

Your execution will take some time to run.

You can check the status of the execution, by sending a GET request to endpoint `$AI_API_URL/v2/lm/executions/<executableId>`.

After the execution has reaches `COMPLETED` status, you can check your results.

The prompt optimization execution outputs the following:

-   A set or metrics that are stored in the tracking service. Post execution completion the metrics can be seen by calling the tracking api. For more information, see [Get Metrics](get-metrics-f7eaf28.md).

-   A set of optimized prompt templates in the prompt registry, one per model. In case the optimization didn’t give better results than the original prompt, no prompt template is stored. You can review the optimized template in the prompt registry. For more information, see [Get a Prompt Template](get-a-prompt-template-bc8cead.md).

-   A log of results contained in an output artifact that is created in the execution. This gets created in the `default` object store.


