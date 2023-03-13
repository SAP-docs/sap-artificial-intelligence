<!-- loio354931f07fd043359a8ea054a75f2648 -->

# View Metrics for a Model

The *Metrics* tab provides an overview of the quality of a model. The metric data is logged by a workflow executable during an execution \(training process\).



<a name="loio354931f07fd043359a8ea054a75f2648__prereq_lmh_lrd_jpb"/>

## Prerequisites

You have the `scenario_artifact_viewer` or `scenario_metric_viewer` role, or you have been assigned a role collection that contains one of these roles.

For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).



<a name="loio354931f07fd043359a8ea054a75f2648__context_hpc_14j_1rb"/>

## Context

Metrics provide data about the quality \(confidence\) of a model. Model quality is affected by the dataset used in the execution \(training process\), which you can check in [Investigate a Model](investigate-a-model-90d641f.md). Metric data can help you to decide whether a model is performing well, and whether it is fit for purpose.

Metric data is common to both the generated models and executions. You can view the same metrics information on the execution's details page. For more information, see [View the Metric Resource for an Execution](view-the-metric-resource-for-an-execution-d85dd44.md).



<a name="loio354931f07fd043359a8ea054a75f2648__steps_qkj_n3p_5nb"/>

## Procedure

1.  In the *ML Operations* app, find the model and display its details see [Investigate a Model](investigate-a-model-90d641f.md).

2.  To view the model metrics, select the *Metrics* tab.

    Metrics details are displayed, as follows:

    -   *Name*: Quality criteria \(model evaluation metrics\). For example, accuracy or mean absolute error \(MSE\).
    -   *Value*: Indicator of quality, which is dependent on the *Name* \(criteria\).
    -   *Timestamp* and *Step*: Used to uniquely identify or differentiate the results. For example, a model can train iteratively using the same dataset in a single training process. Also known as an epoch.
    -   *Labels*: Classifying phrase/ name applied to the metric for that training \(workflow executable\).

    For a detailed comparison of metrics and their performance, see [Compare Model Metrics](compare-model-metrics-4b4415e.md).

    To create a chart to compare models, see [Create Chart to Compare Models](create-chart-to-compare-models-a943fa7.md).


**Related Information**  


[Querying Metric Data](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/f25046fbda39417b8bc66991606b428d.html)

[Storing Metric Data](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/ab04f048da444d13bae08214c9d40e12.html)

[Compare Model Metrics](compare-model-metrics-4b4415e.md "You can compare metrics for models to determine which configuration parameters result in optimum results.")

