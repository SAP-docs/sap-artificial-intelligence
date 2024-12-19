<!-- loiod632ba9a60ab46498b2509f958838461 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Train a Model

In the *Functions Explorer* app, you create a run to train a model.



<a name="loiod632ba9a60ab46498b2509f958838461__prereq_b54_nld_jpb"/>

## Prerequisites

You have the `scenario_job_editor` role, or you are assigned a role collection that contains this role. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).



<a name="loiod632ba9a60ab46498b2509f958838461__context_wnv_kfx_4tb"/>

## Context

The steps to train a model and create a run are the same. A run is the training process that generates a model.

Training a model is an iterative process. You create successive runs with different values for the datasets and parameters in the run template. A configuration combines the dataset values for input, and values for parameters. The quality of the resulting model depends on the specified datasets and parameters in the configuration. You can expect to experiment iteratively with these values until your model reaches the required benchmark.

To determine how configuration parameters are affecting your models, see [Compare Model Metrics](compare-model-metrics-e357639.md).



## Procedure

1.  In the *Functions Explorer* app, find the run template. For more information, see [Investigate a Run Template](investigate-a-run-template-b753dc0.md).

    The *Template Details* screen appears. From here, you can display the configurations, previous runs, and associated contents \(datasets and models\) for the run template.

2.  Choose *Run* to create a new run and generate a new model.

    A wizard appears to assist with the settings for the run. The scenario and run template values are pre-filled based on your previous selections.

3.  Select a configuration.

    -   Search for a configuration in the list by entering a name or part of a name in the :mag: field.

        > ### Tip:  
        > When your runtime is SAP AI Core, this search is not case-sensitive. For other runtimes, search may be case-sensitive.

    -   Select a configuration and confirm the settings using the preview \(right\) pane.
    -   If the existing configurations don't have your required parameters, choose *create a configuration*. See [Create a Configuration](create-a-configuration-c89e279.md).

4.  Choose *Review* to review the details of the run.

5.  Check the settings and choose *Create* to create a new run.

    A run is created and started.

6.  Choose *Refresh* to update the status of the job.

    When the run is complete, a model is generated as output. You can compare the model with other models to determine its quality. See [Compare Model Metrics](compare-model-metrics-e357639.md).


