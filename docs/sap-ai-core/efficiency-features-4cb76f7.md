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





### Reserve Nodes Using a Third-Party API Platform

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





### Check Reserve Node Status Using a Third-Party API Platform

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

**Related Information**  


[Service Plans](service-plans-c7244c6.md "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.")

