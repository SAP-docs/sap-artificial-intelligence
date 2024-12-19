<!-- loio4cb76f72827240ec80eb53f1a7496ccf -->

# Efficiency Features

Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.



<a name="loio4cb76f72827240ec80eb53f1a7496ccf__section_y5q_swb_gxb"/>

## Tenant Warm Node Pool

Tenant warm nodes allow tenants to reserve nodes from specific resource plan types, ensuring that a predefined number of nodes exist in the cluster. The reserved nodes can then be used during model training and serving. Reserving nodes reduces waiting time at workload startup, but incurs costs in line with node use, whether consumed or not.



### Mechanism of Node Reservation

1.  The tenant specifies number of nodes to reserve.
2.  An execution or deployment utilizes a reserved node, a replacement reserve node of the same resource plan type is requested from the hyperscaler.

The number of reserved nodes specified by the tenant are consistently available for use.

The minimum number of reserved nodes is 0.



### About Node Reservation

-   The number of reserved nodes specified by the tenant are consistently available for use.
-   The minimum number of reserved nodes is 0.
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

**Parent topic:**[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[Workflow Templates](workflow-templates-83523ab.md "Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.")

[List Scenarios](list-scenarios-deedde5.md "A scenario is an implementation of a specific AI use case within a user's tenant. It consists of a pre-defined set of AI capabilities in the form of executables and templates.")

[List Executables](list-executables-80895a4.md "An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts (datasets or models) and parameters (custom key-pair values) that enable the template to be reused in different scenarios.")

[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references (such as datasets or models), and environment settings that are used to instantiate and run an execution or deployment of an executable or template.")

[List Configurations](list-configurations-8074b2a.md "")

[Using Artifact Signatures](using-artifact-signatures-2f02a1d.md "Artifact signatures in the form of a hash can be added to output artifacts from executions.")

[Start Training](start-training-54b44e4.md "")

[Stop Training Instances](stop-training-instances-3d85344.md "")

[Delete Training Instances](delete-training-instances-612ce17.md "")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "accessed in the deployment and execution logs.")

[Training Schedules](training-schedules-2b702f8.md "")

[Service Plans](service-plans-c7244c6.md "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.")

