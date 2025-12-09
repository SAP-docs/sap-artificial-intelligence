<!-- loioacfce87917654ac5a139a10e2d57b448 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# View Prompt Optimization Run Details



<a name="loioacfce87917654ac5a139a10e2d57b448__prereq_vp3_r2g_s2c"/>

## Prerequisites

-   You have the `custom_evaluation`, `genai_manager` or `genai_experimenter` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

-   You have deployed a prompt optimization. For more information, see [Create a Prompt Optimization](create-a-prompt-optimization-0b920f6.md).

-   You're using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app and choose the resource group that was used for your generative AI hub deployment.

2.  In the side navigation, expand the *Generative AI Hub* and choose *Optimizations*.

3.  Choose the *Runs* tab and expand the optimization that you want to view.

    You can filter by name or by using tags by using the <span class="SAP-icons-V5"></span> \(Filter\)icon. Your input must be an exact match.

    You can view the winning optimization candidate by expanding the run and choosing the child node.

    The *Run Details* will open.

    You will see references to your output artifact and details of the optimized prompt template.




<a name="loioacfce87917654ac5a139a10e2d57b448__postreq_nnz_tjg_s2c"/>

## Next Steps

You can refresh the view using the <span class="SAP-icons-V5"></span> \(Refresh\) icon.

You can add more tags to your prompt optimization using the :heavy_plus_sign: icon.

You can edit the values of existing tags using the :pencil2: icon, and delete existing tags using the :wastebasket: icon.

You can delete a prompt optimization using the :wastebasket: button.

