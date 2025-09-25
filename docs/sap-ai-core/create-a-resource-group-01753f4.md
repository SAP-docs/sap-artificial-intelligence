<!-- loio01753f4dcb454401b539ecc4def641be -->

# Create a Resource Group

**Parent topic:**[Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group is a unique dedicated namespace or workspace environment, where users can create or add configurations, executions, deployments, and artifacts. They are used for running training jobs or model servers.")

**Related Information**  


[Edit a Resource Group](edit-a-resource-group-3f88c30.md "")

[Delete a Resource Group](delete-a-resource-group-40d83a2.md "")

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__prereq_gfy_kzc_gyb"/>

## Prerequisites

You've completed the initial setup. For more information, see [Initial Setup](initial-setup-38c4599.md).

You have access to a public-facing Docker registry over the internet. It isn't possible to use a Docker registry behind a VPN or corporate network.



<a name="task_i3h_n13_tcc__context_mqx_wzw_kxb"/>

## Context

> ### Note:  
> Resource group Ids must be of length minimum: 3, maximum: 253. The first and last characters must be either a lowercase letter, an uppercase letter, or a number. Character entries from the second to penultimate can include a lower case letter, an upper case letter, a number, a period \(.\), or a hyphen \(-\). No other special characters are permitted.



<a name="task_i3h_n13_tcc__steps_icj_ncy_ycc"/>

## Procedure

Create a resource group by sending the following:

```
curl --location --request POST "$AI_API_URL/v2/admin/resourceGroups" --header "Authorization: Bearer $TOKEN" --header 'Content-Type: application/json' --data-raw '{ "resourceGroupId": "<ID of your resource group>"}'

```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__prereq_awy_b3d_gyb"/>

## Prerequisites

You've completed the initial setup. For more information, see [Initial Setup](initial-setup-38c4599.md).

You have access to a public-facing Docker registry over the internet. It isn't possible to use a Docker registry behind a VPN or corporate network.



<a name="task_cxf_n13_tcc__context_zyr_lcy_ycc"/>

## Context

> ### Note:  
> Resource group Ids must be of length minimum: 3, maximum: 253. The first and last characters must be either a lowercase letter, an uppercase letter, or a number. Character entries from the second to penultimate can include a lower case letter, an upper case letter, a number, a period \(.\), or a hyphen \(-\). No other special characters are permitted.



<a name="task_cxf_n13_tcc__steps_azr_lcy_ycc"/>

## Procedure

1.  As the request body, select the *raw* radio button and enter the following:

    ```json
    {
        "resourceGroupId": "<ID of your resource group>"
    }
    ```

2.  Send the request.




<a name="task_cxf_n13_tcc__result_pqb_szw_kxb"/>

## Results

You'll receive a 202 response to confirm that the request to create the resource group has been accepted.

