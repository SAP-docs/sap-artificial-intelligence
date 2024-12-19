<!-- loioebc3f5ca96044937ab1aa73ee0c3fb53 -->

# Create a Run

A run is a training process that uses a run template and a configuration to generate a model.



<a name="loioebc3f5ca96044937ab1aa73ee0c3fb53__prereq_pyq_m1t_yqb"/>

## Prerequisites

You have the `scenario_job_editor` role, or you have been assigned a role collection that contains this role.

For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).



<a name="loioebc3f5ca96044937ab1aa73ee0c3fb53__context_wtk_jdf_wtb"/>

## Context

Runs are used to train a model.



<a name="loioebc3f5ca96044937ab1aa73ee0c3fb53__steps_rc4_mzw_xtb"/>

## Procedure

1.  In the *Functions Explorer* app, choose *All Scenarios*.

2.  Find the run template and display its details. For more information, see [Investigate a Run Template](investigate-a-run-template-b753dc0.md).

3.  Choose *Run* to create a new run.

    The *Create New Run* wizard appears. This wizard has four steps.

4.  Select the required data for the new run. Note, the scenario and run template are prefilled from your previous selections.

    1.  In the *Select Configuration* step, select the required configuration. The details for the selected configuration are displayed in the right pane. Confirm the selection and choose *Review*.

        > ### Tip:  
        > If there is no configuration which matches your data requirements, you can choose *create a configuration*. The run you have started will be lost, and you will be redirected to create a configuration. When you have saved the new configuration, you can re-create the run with the new configuration. See [Create a Configuration](create-a-configuration-c89e279.md).

    2.  In the *Review* step, review the data that you've selected for the new run. Choose *Create* to create the run.


    The new run is created.


-   **[Create a Configuration](create-a-configuration-c89e279.md "A configuration contains parameters and dataset references, and is combined with a run
		template to create a run.")**  
A configuration contains parameters and dataset references, and is combined with a run template to create a run.

**Related Information**  


[Find a Run](find-a-run-58bfae5.md "You can find a run and explore its details.")

[Investigate a Run](investigate-a-run-e479244.md "You can explore run details for detailed insights about the training process for a model.")

[Runs](runs-396875a.md "A run is a training process that generates a model or models. A run is an instance of a run template (an AI pipeline), created using a configuration.")

