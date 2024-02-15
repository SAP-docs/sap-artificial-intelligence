<!-- loio9fad26a7e6894e3cbd80da723ce466fc -->

# Efficiency Features

Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.



<a name="loio9fad26a7e6894e3cbd80da723ce466fc__section_grr_bbf_1xb"/>

## Autoscaling

SAP AI Core includes parameters to reduce the number of nodes used based on current consumption, or impose usage limits during periods of high consumption. These parameters allow your workload the flexibility to scale based on demand, and for consumption to be capped, limiting your consumption and therefore costs. For more information, see [Serving Templates](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



<a name="loio9fad26a7e6894e3cbd80da723ce466fc__section_k1v_fbf_1xb"/>

## Scaling to 0

Where non-uniform loads are expected, scaling to 0 allows nodes to enter a sleeping state when demand allows, limiting your consumption, and therefore costs. Nodes wake when demand increases, which has an increased response time. The Global Node pool reduces, this cold start time. For more information, see [Serving Templates](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



<a name="loio9fad26a7e6894e3cbd80da723ce466fc__section_mgb_kbf_1xb"/>

## Global Node Pool

When the inference server scales up from a sleeping state, there is some additional response time. To reduce this, SAP AI Core has a Global Node Pool, which keeps commonly used nodes reserved to allow for shorter response times. You do not need to do anything to make use of the Global Node Pool, it is already in place. To reduce response times further, avoid a cold start altogether by setting your autoscaling parameter to `1`. For more information, see [Serving Templates](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



<a name="loio9fad26a7e6894e3cbd80da723ce466fc__section_krp_lbf_1xb"/>

## Scaling to 1

Cold starts can be avoided completely by scaling to `1`. This keeps a single node warm, even when it is not needed, reducing response time. However, it does not offer the consumption and cost savings associated with scaling to 0. For more information, see [Serving Templates](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



## Duration

The default duration is indefinite, however the `ttl` parameter limits the duration of a deployment to minutes, hours, or days. This parameter allows you to plan the deletion if your model servers and model deployment URL, allowing for an expected period of use and avoiding unnecessary consumption and costs afterwards. For more information, see [Deploy Models](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD) and [About the AI API](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



<a name="loio9fad26a7e6894e3cbd80da723ce466fc__section_d11_vwb_gxb"/>

## Tenant Warm Node Pool

Tenant warm nodes allows tenants to reserve nodes from specific resource plan types, ensuring that a predefined number of nodes exist in the cluster. The reserved nodes can then be used during model training and serving. Reserving nodes reduces waiting time at workload startup, but incurs costs inline with node use, whether consumed or not.



### Mechanism of Node Reservation

1.  The tenant specifies number of nodes to reserve.
2.  An execution or deployment utilizes a reserved node, a replacement reserve node of the same resource plan type is requested from the hyperscaler.

The number of reserved nodes specified by the tenant are consistently available for use.

The minumum number of reserved nodes is 0.



### About Node Reservation

-   The number of reserved nodes specified by the tenant are consistently available for use.
-   The minumum number of reserved nodes is 0.
-   The maximum number of reserved nodes is 10.
-   The default number of reserved nodes is 0.





### Reserve Nodes Using Postman

1.  Send a PATCH request to the endpoint`{{apiurl}}/v2/admin/resources/nodes`
2.  Provide the resource plan type and quantity of nodes to reserve in the request body in JSON format:

    ```
    {
        "resourcePlans": [
            {
                "name": "infer.l",
                "request": 1
            },
            {
                "name": "infer.m",
                "request": 1
            },
            {
                "name": "train.l",
                "request": 1
            }
            ...
        ]
    }
    ```




### Reserve Nodes Using curl

Submit a PATCH request to the endpoint`{{apiurl}}/v2/admin/resources/nodes`

```
curl --request PATCH $AI_API_URL/v2/admin/resources/nodes \
--data-raw '{
    "resourcePlans": [
        {
            "name": "infer.l",
            "request": 1
        },
        {
            "name": "infer.m",
            "request": 1
        },
        {
            "name": "train.l",
            "request": 1
        }
    ]
}'

```

> ### Remember:  
> All reserved nodes are charged at the same rate as nodes used during model training and serving.





### Check Reserve Node Status Using Postman

Send a GET request to the endpoint`{{apiurl}}/v2/admin/resources/nodes`



### Check Reserve Node Status Using curl

```
curl --request GET $AI_API_URL/v2/resources/nodes
```

> ### Output Code:  
> ```
> {
>     "resourcePlans": {
>         "infer.l": {
>             "provisioned": 1,
>             "requested": 1
>         },
>         "infer.m": {
>             "provisioned": 1,
>             "requested": 1
>         },
>         "train.l": {
>             "provisioned": 1,
>             "requested": 1
>         }
>     }
> }
> ```

-   `requested`: the number of reserve nodes requested by the tenant.
-   `provisioned`: the number of reserve nodes that are currently present in the cluster.



### Update Quantities of Reserved Nodes

To update the number of nodes reserved, repeat the reservation procedure, with updated quantities in the `request` field.



### Delete Reserved Nodes

To delete reserved nodes, repeat the reservation procedure, with quantities in the `request` field set to *0*.

**Parent topic:**[Use Your Model](use-your-model-7f93e8f.md "You deploy your AI learning model to run inferences against it.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-abd672f.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.")

[List Executables](list-executables-6af8e60.md "An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a resource group and get details of specific executables from a resource group. Serving templates are mapped to deployment executables.")

[Deploy Models](deploy-models-dd16e8e.md "")

[Inferencing](inferencing-e348ecf.md "")

[Update a Deployment](update-a-deployment-9789ddd.md "")

[Stop Deployments](stop-deployments-b7d2577.md " ")

[Delete Deployments](delete-deployments-0193d17.md " ")

[Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md "accessed in the deployment and execution logs.")

[Service Plans](service-plans-c7244c6.md "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.")

