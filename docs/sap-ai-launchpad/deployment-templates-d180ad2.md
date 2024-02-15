<!-- loiod180ad2c4e3246b2becfc14c8b31e697 -->

# Deployment Templates

A deployment template is used to deploy an AI model.

A deployment template defines placeholders for key data such as:

-   Model \(in most cases\)

-   Parameters

-   Hyperparameter values for the model \(variables that affect the decision-making capability of the model\)

-   Efficiency parameters


Values for parameters and other inputs are provided by a configuration. To start the deployment process with these values, a deployment is created with the configuration.

-   **[Investigate a Deployment Template](investigate-a-deployment-template-0f68ee0.md "Use the Functions
                                    Explorer app to
		view a list of deployment templates, and explore a template in detail.")**  
Use the *Functions Explorer* app to view a list of deployment templates, and explore a template in detail.
-   **[Find a Configuration](find-a-configuration-642037f.md "You can view all the configurations associated with a deployment template, and
		investigate a configuration in detail.  ")**  
You can view all the configurations associated with a deployment template, and investigate a configuration in detail.
-   **[Find a Deployment](find-a-deployment-94f81c1.md "You can find a deployment and display its details.")**  
You can find a deployment and display its details.
-   **[Create a Deployment](create-a-deployment-081b1a8.md "A deployment uses a model and data to make a prediction.")**  
A deployment uses a model and data to make a prediction.

<a name="concept_fys_gff_1xb"/>

<!-- concept\_fys\_gff\_1xb -->

## Efficiency Features in the SAP AI Core Runtime

In addition, the SAP AI Core runtime that improve model server efficiency and help manage resource consumption during the deployment.



<a name="concept_fys_gff_1xb__section_grr_bbf_1xb"/>

## Autoscaling

SAP AI Core includes parameters to reduce the number of nodes used based on current consumption, or impose usage limits during periods of high consumption. These parameters allow your workload the flexibility to scale based on demand, and for consumption to be capped, limiting your consumption and therefore costs. For more information, see [Serving Templates](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



<a name="concept_fys_gff_1xb__section_k1v_fbf_1xb"/>

## Scaling to 0

Where non-uniform loads are expected, scaling to 0 allows nodes to enter a sleeping state when demand allows, limiting your consumption, and therefore costs. Nodes wake when demand increases, which has an increased response time. The Global Node pool reduces, this cold start time. For more information, see [Serving Templates](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



<a name="concept_fys_gff_1xb__section_mgb_kbf_1xb"/>

## Global Node Pool

When the inference server scales up from a sleeping state, there is some additional response time. To reduce this, SAP AI Core has a Global Node Pool, which keeps commonly used nodes reserved to allow for shorter response times. You do not need to do anything to make use of the Global Node Pool, it is already in place. To reduce response times further, avoid a cold start altogether by setting your autoscaling parameter to `1`. For more information, see [Serving Templates](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



<a name="concept_fys_gff_1xb__section_krp_lbf_1xb"/>

## Scaling to 1

Cold starts can be avoided completely by scaling to `1`. This keeps a single node warm, even when it is not needed, reducing response time. However, it does not offer the consumption and cost savings associated with scaling to 0. For more information, see [Serving Templates](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).



<a name="concept_fys_gff_1xb__section_tfv_pbf_1xb"/>

## Duration

The default duration is indefinite, however the `ttl` parameter limits the duration of a deployment to minutes, hours, or days. This parameter allows you to plan the deletion if your model servers and model deployment URL, allowing for an expected period of use and avoiding unnecessary consumption and costs afterwards. For more information, see [Deploy Models](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD) and [About the AI API](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).

