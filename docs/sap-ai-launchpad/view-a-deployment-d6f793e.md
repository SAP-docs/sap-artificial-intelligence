<!-- loiod6f793e11145488daac3d1b7229a052a -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# View a Deployment

You can view the lifecycle details for a deployment, and explore details for each operation in the deployment.



<a name="loiod6f793e11145488daac3d1b7229a052a__prereq_b54_nld_jpb"/>

## Prerequisites

You have the `mloperations_viewer` or `scenario_deployment_viewer` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).



<a name="loiod6f793e11145488daac3d1b7229a052a__steps_qkj_n3p_5nb"/>

## Procedure

1.  Choose a resource group. For more information, see [Set Resource Group](set-resource-group-0c07728.md#loio0c077289f29d4147921fb07ab0f68b7f).

2.  In the *ML Operations* app, choose *Deployments*.

    The *All Deployments* screen appears listing all of the deployments for the selected resource group. Deployments are listed by ID, and with additional details such as configuration name and ID, current and target status, created on timestamp, and changed on timestamp.

    > ### Note:  
    > If your runtime supports deployment durations, you'll see running until dates. Deployments run until this time, and are then automatically stopped and deleted.

3.  **Optional:** Filter the list by choosing <span class="SAP-icons"></span> \(Filter\). The *Filter* dialog appears.

    1.  Enter a deployment ID, if required. A valid deployment ID consists of lowercase characters, hyphens \(-\), and numbers.

    2.  Alternatively, enter a configuration ID or status, or choose a scenario and additional attributes, such as version and executable.

    3.  Choose *Apply* to apply the filter and conditions to the list.


4.  To view the details for an individual deployment, select the deployment in the list or choose <span class="SAP-icons"></span> \(More\).

    You'll see an overview of the deployment lifecycle process.

    ![Details screen for a pending deployment.](images/Image_AIL_Deployment_Enhanced_Tabs_Fullscreen_760e4b2.png)

    > ### Tip:  
    > Timestamp details for each step in the deployment process can be seen in the header. These dates and times show when the deployment was created, submitted, started, and finished. The process duration is also displayed. Timestamps are displayed in the user's local time zone.
    > 
    > If your runtime supports deployment durations, you'll see a running until date. If a deployment is not complete by this time it will be automatically stopped and deleted.
    > 
    > The *URL* is the endpoint used to make predictions.
    > 
    > The *Overview* tab shows the operations involved in the deployment, as well as summary data, such as ID. You can click each card in the process overview to display the specific operation in more detail.

5.  **Optional:** Choose the *Status* tab to check detailed message, status, and severity information for the deployment. See [View Status Details](view-status-details-7bda8db.md).

6.  **Optional:** When your runtime is SAP AI Core, you can choose the *Scaling* tab to check the replica limits, and the number of running replicas for the deployment.

    ![Scaling tab with replica details shown.](images/Image_AIL_Deployment_Scaling_f65fdf7.png)

    > ### Tip:  
    > A running deployment on a given node is called a replica. Replicas are used in distributed model training. For performance reasons, there are limits on the number of running replicas. You check how many replicas are running for a model deployment to better understand performance.

7.  **Optional:** When your runtime is SAP AI Core, you can choose the *Resources* tab to check what resource plan applies to the deployment.

    ![Resources tab with starter resource plan shown.](images/Image_AIL_Deployment_Resources_74d710f.png)

    > ### Tip:  
    > A resource plan is a preconfigured infrastructure bundle that is used to process an AI operation, such as a deployment. Different operations within an AI workflow can use different resource plans.

8.  **Optional:** Choose the *Logs* tab to check or download the logs for the deployment. See [View Deployment Logs](view-deployment-logs-4f9682e.md).


**Related Information**  


[Update a Deployment](update-a-deployment-bce2b16.md "You can update a deployment with your choice of configuration.")

[Deploy Models](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/dd16e8ef75654dde831e7b812688e4fa.html "Utilize your model and retrieve a URL to use for inferencing.") :arrow_upper_right:

[Choose a Resource Plan](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/57f4f19d9b3b46208ee1d72017d0eab6.html "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called &quot;resource plans&quot; for this purpose.") :arrow_upper_right:

