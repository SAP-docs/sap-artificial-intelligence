<!-- loioc89e27943ed24e258c2aa225ef0d18c4 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Create a Configuration

A configuration contains parameters and dataset references, and is combined with a run template to create a run.



<a name="loioc89e27943ed24e258c2aa225ef0d18c4__prereq_b54_nld_zzc"/>

## Prerequisites

You have the `scenario_configuration_editor` role, or you have been assigned a role collection that contains this role.

For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).



## Procedure

1.  Find the run template. For more information, see [Investigate a Run Template](investigate-a-run-template-b753dc0.md)

2.  Select the *Available Configurations* tab.

    This lists all configurations by name and ID, and with creation date details.

3.  Choose *Create* to create a new configuration.

    The *Create Configuration* wizard appears. This wizard has four steps.

4.  Enter the required data for the new configuration.

    1.  In the *Enter Name* step, enter a configuration name and choose *Next*.

    2.  In the *Input Parameters* step, enter the input parameter values \(alphanumeric\) for the selected job executable, then choose *Next*.

        > ### Restriction:  
        > A configuration can contain up to 1000 input parameters. An input parameter value can't exceed 5000 characters.

    3.  In the *Input Contents* step, find the name of the dataset in the list of *Available Contents* list \(right pane\).

        To search for a dataset, enter a value or partial value in the :mag:field.

        For the selected dataset, choose the dropdown for the *Assignment* field and select the input.

    4.  Choose *Review* to display a summary of the configuration details. Choose *Create* to create the configuration.

    The newly created configuration and its details are displayed.


**Related Information**  


[Find a Configuration](find-a-configuration-3f1d78d.md "You can view all the configurations associated with a run template, and investigate a configuration in detail.")

