<!-- loiodb2da6d9cc2649bdb7140609418e1907 -->

# Create a Tabular AI Deployment

Create a configuration and deployment in SAP AI Core to access tabular orchestration.



## Prerequisites

-   You have an SAP AI Core service instance and service key. For more information, see [SAP AI Core Initial Setup Documentation](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/38c4599432d74c1d94e70f7c955a717d.html?locale=en-US&state=PRODUCTION&version=CLOUD).
-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.
-   You have created a resource group. For more information, see[Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   Make sure that you've set the following headers:


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
    

> ### Note:  
> Use the same resource group for all generative AI activities. To use a different resource group, repeat these steps for each resource group.



## Access Tabular Orchestration

-   Create a configuration

-   Create a deployment

-   When the deployment reaches the `RUNNING` state, retrieve the `deploymentUrl`.

-   Use the `deploymentUrl` to access tabular orchestration.




## Check Scenario and Executable



### Check Scenario

Check that you have access to the `tabular-orchestration` scenario:

```
curl GET "$AI_API_URL/v2/lm/scenarios/tabular-orchestration" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN"
```

**Result**

You receive a successful response including the scenario ID `tabular-orchestration`.



### Check Executable

Check that you have access to the `tabular-orchestration` executable:

```
curl GET "$AI_API_URL/v2/lm/scenarios/tabular-orchestration/executables/tabular-orchestration" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN"
```

**Result**

You receive a successful response including the executable ID `tabular-orchestration`.



## Create a Configuration

Send a POST request to create a configuration:

```
curl POST "$AI_API_URL/v2/lm/configurations" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "name": "<yourNameChoice>",
    "executableId": "tabular-orchestration",
    "scenarioId": "tabular-orchestration"
  }'
```

**Result**

You receive a unique `configurationId` in the response. Set the variable `CONFIGURATION_ID` to this value.



## Create a Deployment

Send a POST request to create a deployment:

```
curl POST "$AI_API_URL/v2/lm/deployments" \
  --header "AI-Resource-Group: $RESOURCE_GROUP_ID" \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "configurationId": "<yourConfigurationId>"
  }'
```

**Result**

You receive a unique `deploymentId` in the response. Set the variable `DEPLOYMENT_ID` to this value.



## Next Steps

Retrieve the details of your deployment by sending a GET request:

```
curl GET "$AI_API_URL/v2/lm/deployments/{deploymentId}"
```

When the deployment reaches the `RUNNING` state, note the `deploymentUrl` in the response.

Use the `deploymentUrl` to access tabular orchestration.

