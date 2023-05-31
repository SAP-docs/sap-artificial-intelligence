<!-- loio4ef8499d7a4945ec854e3b4590830bcc -->

# Roles and Authorizations

SAP AI Launchpad provides default role collections that you can assign to users. The role collections determine which actions a user is able to carry out in SAP AI Launchpad. You can also create your own role collections and assign the required roles to them.



SAP AI Launchpad provides standard or default role collections. The default role collections bundle the roles required for likely SAP AI Launchpad tasks and app functions. However, if these role collections do not suit your organizational needs, you can create your own role collections.

**Default Role Collections**


<table>
<tr>
<th valign="top">

Relevance



</th>
<th valign="top">

Default Role Collection



</th>
<th valign="top">

Description



</th>
<th valign="top">

Includes Roles



</th>
</tr>
<tr>
<td valign="top">

 SAP AI Launchpad 



</td>
<td valign="top">

 `ailaunchpad_connections_editor` 



</td>
<td valign="top">

Provides roles to view, create, edit, and delete connections to your AI runtime \(for example, SAP AI Core\)



</td>
<td valign="top">

`viewer`

`connections_editor`



</td>
</tr>
<tr>
<td valign="top">

 SAP AI Launchpad 



</td>
<td valign="top">

 `ailaunchpad_allow_all_resourcegroups` 



</td>
<td valign="top">

Provides access to all resource groups



</td>
<td valign="top">

 `allow_all_resourcegroups` 



</td>
</tr>
<tr>
<td valign="top">

 *ML Operations* app



</td>
<td valign="top">

 `ailaunchpad_mloperations_viewer` 



</td>
<td valign="top">

Provides roles to view all contents of scenarios and resource groups



</td>
<td valign="top">

`viewer`

`mloperations_viewer`



</td>
</tr>
<tr>
<td valign="top">

 *ML Operations* app



</td>
<td valign="top">

 `ailaunchpad_mloperations_editor` 



</td>
<td valign="top">

Provides roles to view all contents of scenarios, and to view and edit contents of resource groups



</td>
<td valign="top">

`viewer`

`mloperations_editor`

`artifact.register`



</td>
</tr>
<tr>
<td valign="top">

*SAP AI Core Administration* app



</td>
<td valign="top">

`ailaunchpad_aicore_admin_viewer`



</td>
<td valign="top">

Provides roles to view authentications required for AI workflows involving SAP AI Core \(AI runtime\)



</td>
<td valign="top">

 `aicore_admin_viewer_all` 



</td>
</tr>
<tr>
<td valign="top">

*SAP AI Core Administration* app



</td>
<td valign="top">

`ailaunchpad_aicore_admin_editor`



</td>
<td valign="top">

Provides roles to edit authentications required for AI workflows involving SAP AI Core \(AI runtime\)



</td>
<td valign="top">

 `aicore_admin_editor_all` 



</td>
</tr>
<tr>
<td valign="top">

 *Functions Explorer* app



</td>
<td valign="top">

 `ailaunchpad_functions_explorer_viewer_v2` 



</td>
<td valign="top">

Provides roles to view scenarios and all ML resources of a scenario



</td>
<td valign="top">

`viewer`

`connections_viewer`

`functions_explorer`

`mlfunctions_viewer`

`scenario_executable_viewer`

`scenario_metadata_viewer`

`scenario_configuration_viewer`

`scenario_job_viewer`

`scenario_artifact_viewer`

`scenario_metric_viewer`



</td>
</tr>
<tr>
<td valign="top">

 *Functions Explorer* 



</td>
<td valign="top">

 `ailaunchpad_functions_explorer_editor_v2` 



</td>
<td valign="top">

Edit scenarios and all ML resources of a scenario



</td>
<td valign="top">

`viewer`

`connections_viewer`

`functions_explorer`

`mlfunctions_editor`

`scenario_executable_viewer`

`scenario_metadata_viewer`

`scenario_metric_viewer`

`scenario_configuration_editor`

`scenario_job_editor`

`scenario_artifact_editor`



</td>
</tr>
</table>



If you want to create your own role collections, you can assign roles to them based on the following table.

**Default Roles**


<table>
<tr>
<th valign="top">

Role



</th>
<th valign="top">

Allows Users To



</th>
</tr>
<tr>
<td valign="top">

`allow_connections`



</td>
<td valign="top">

Manage custom access to runtime connections in SAP AI Launchpad



</td>
</tr>
<tr>
<td valign="top">

`connections_viewer`



</td>
<td valign="top">

View runtime connections in SAP AI Launchpad



</td>
</tr>
<tr>
<td valign="top">

`connections_editor`



</td>
<td valign="top">

Edit runtime connections in SAP AI Launchpad



</td>
</tr>
<tr>
<td valign="top">

`viewer`



</td>
<td valign="top">

Access SAP AI Launchpad \(default role for all users\)



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_repositories_viewer`



</td>
<td valign="top">

View Git repositories in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_repositories_editor`



</td>
<td valign="top">

Add, edit, or remove Git repositories in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_applications_viewer`



</td>
<td valign="top">

View applications in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_applications_editor`



</td>
<td valign="top">

Create, edit, or delete applications in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_dockerregistrysecret_viewer`



</td>
<td valign="top">

View Docker registry secrets in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_dockerregistrysecret_editor`



</td>
<td valign="top">

Add, edit, or remove Docker registry secrets in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_resourcegroup_viewer`



</td>
<td valign="top">

View resource groups in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_resourcegroup_editor`



</td>
<td valign="top">

Create, edit, or delete resource groups in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_objectstoresecret_viewer`



</td>
<td valign="top">

View object store secrets in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_objectstoresecret_editor`



</td>
<td valign="top">

Add, edit, or remove object store secrets in the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`scenario_metadata_viewer`



</td>
<td valign="top">

View scenarios and scenario versions



</td>
</tr>
<tr>
<td valign="top">

`scenario_executable_viewer`



</td>
<td valign="top">

View executables of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_configuration_viewer`



</td>
<td valign="top">

View configurations of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_configuration_editor`



</td>
<td valign="top">

Edit configurations of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_deployment_viewer`



</td>
<td valign="top">

View deployments of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_deployment_editor`



</td>
<td valign="top">

Edit deployments of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_deployment_predictor`



</td>
<td valign="top">

Invoke deployments of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_execution_viewer`



</td>
<td valign="top">

View executions of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_execution_editor`



</td>
<td valign="top">

Edit executions of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_artifact_viewer`



</td>
<td valign="top">

View artifacts of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_artifact_editor`



</td>
<td valign="top">

Edit artifacts of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_metric_viewer`



</td>
<td valign="top">

View tracking metrics of an execution



</td>
</tr>
<tr>
<td valign="top">

`resourcegroup_viewer`



</td>
<td valign="top">

View resource groups



</td>
</tr>
<tr>
<td valign="top">

`allow_all_resourcegroups`



</td>
<td valign="top">

Template for allowing access to all resource groups for a connection



</td>
</tr>
<tr>
<td valign="top">

`functions_explorer`



</td>
<td valign="top">

Template for viewing functions explorer for SAP AI Launchpad



</td>
</tr>
<tr>
<td valign="top">

`operations_manager`



</td>
<td valign="top">

Template for viewing operations manager for SAP AI Launchpad



</td>
</tr>
<tr>
<td valign="top">

`scenario_job_viewer`



</td>
<td valign="top">

View jobs of a scenario



</td>
</tr>
<tr>
<td valign="top">

`scenario_job_editor`



</td>
<td valign="top">

Edit jobs of a scenario



</td>
</tr>
<tr>
<td valign="top">

`mloperations_viewer`



</td>
<td valign="top">

Viewer role for *ML Operations* app



</td>
</tr>
<tr>
<td valign="top">

`mloperations_editor`



</td>
<td valign="top">

Editor role for *ML Operations* app



</td>
</tr>
<tr>
<td valign="top">

`artifact_register`



</td>
<td valign="top">

Register artifacts in *ML Operations* app



</td>
</tr>
<tr>
<td valign="top">

`mlfunctions_viewer`



</td>
<td valign="top">

Viewer role *Functions Explorer* app



</td>
</tr>
<tr>
<td valign="top">

`mlfunctions_editor`



</td>
<td valign="top">

Editor role *Functions Explorer* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_viewer_all`



</td>
<td valign="top">

Viewer role *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`aicore_admin_editor_all`



</td>
<td valign="top">

Editor role *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

`execution_schedules_editor`



</td>
<td valign="top">

Edit execution schedules



</td>
</tr>
<tr>
<td valign="top">

`execution_schedules_viewer`



</td>
<td valign="top">

View execution schedules



</td>
</tr>
<tr>
<td valign="top">

aicore\_admin\_genericsecret\_editor



</td>
<td valign="top">

Create, edit or delete generic secrets in the SAP AI Core runtime through the *SAP AI Core Administration* app



</td>
</tr>
<tr>
<td valign="top">

aicore\_admin\_genericsecret\_viewer



</td>
<td valign="top">

View generic secrets in the SAP AI Core runtime through the *SAP AI Core Administration* app



</td>
</tr>
</table>

**Related Information**  


[Functions Explorer](functions-explorer-90586e6.md "")

[Workspaces](workspaces-6bde2c8.md "The Workspaces app is a dashboard to manage the connection between SAP AI Launchpad and subscribed AI services.")

[Administration](administration-cb4dd1e.md "You use the SAP AI Core Administration app in SAP AI Launchpad to manage administration activities for your SAP AI Core runtime.")

