<!-- loioe7909866a6294b4ab9974dcebc8336f4 -->

# Roles and Authorizations

SAP AI Core provides default role collections that you can assign to users. The role collections determine which actions a user is able to carry out in SAP AI Core. You can also create your own role collections and assign the required roles to them.



<a name="loioe7909866a6294b4ab9974dcebc8336f4__section_yds_rgf_3gb"/>

## Default Roles

SAP AI Core provides the following default roles:

**Default Roles**


<table>
<tr>
<th valign="top">

Role

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`aicore_resourcegroup_viewer` 

</td>
<td valign="top">

View resource groups of the SAP AI Core tenant

</td>
</tr>
<tr>
<td valign="top">

`aicore_resourcegroup_editor view` 

</td>
<td valign="top">

Create and delete resource groups of the SAP AI Core tenant

</td>
</tr>
<tr>
<td valign="top">

`aicore_repository_viewer` 

</td>
<td valign="top">

View GitOps repositories of the SAP AI Core tenant

</td>
</tr>
<tr>
<td valign="top">

`aicore_repository_admin view` 

</td>
<td valign="top">

Create, update, and delete GitOps repositories of the SAP AI Core tenant

</td>
</tr>
<tr>
<td valign="top">

`aicore_application_viewer` 

</td>
<td valign="top">

View GitOps applications of the SAP AI Core tenant

</td>
</tr>
<tr>
<td valign="top">

`aicore_application_admin view` 

</td>
<td valign="top">

Create, update, and delete GitOps applications of the SAP AI Core tenant

</td>
</tr>
<tr>
<td valign="top">

`aicore_log_viewer` 

</td>
<td valign="top">

View application logs of the SAP AI Core tenant

</td>
</tr>
<tr>
<td valign="top">

`aicore_credential_viewer` 

</td>
<td valign="top">

View object store credentials and docker registry credentials \(metadata only\) of the SAP AI Core tenant

</td>
</tr>
<tr>
<td valign="top">

`aicore_credential_admin` 

</td>
<td valign="top">

View, create, update, and delete object store credentials and docker registry credentials \(metadata only\) of the SAP AI Core tenant

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

View or list deployments

</td>
</tr>
<tr>
<td valign="top">

`scenario_deployment_editor view` 

</td>
<td valign="top">

Create, update, and delete deployments; view the application logs of the deployments

</td>
</tr>
<tr>
<td valign="top">

`scenario_deployment_predictor` 

</td>
<td valign="top">

Invoke deployments of a scenario \(for model inference purposes\)

</td>
</tr>
<tr>
<td valign="top">

`scenario_execution_viewer` 

</td>
<td valign="top">

View executions of a scenario and view tracking metrics

</td>
</tr>
<tr>
<td valign="top">

`scenario_execution_editor view` 

</td>
<td valign="top">

Create, update, and delete executions and tracking metrics; view the application logs of the executions

</td>
</tr>
<tr>
<td valign="top">

`scenario_artifact_viewer`

</td>
<td valign="top">

View or list artifacts

</td>
</tr>
<tr>
<td valign="top">

`scenario_artifact_editor`

</td>
<td valign="top">

View, create, update, and delete artifacts

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
</table>



<a name="loioe7909866a6294b4ab9974dcebc8336f4__section_hzq_jkf_3rb"/>

## Role Collections

SAP AI Core provides the following default role collections:

**Role Collections and Roles**


<table>
<tr>
<th valign="top">

Role Collection

</th>
<th valign="top">

Roles

</th>
</tr>
<tr>
<td valign="top">

`aicore_viewer`

</td>
<td valign="top">

-   `scenario_metadata_viewer`

-   `scenario_executable_viewer`

-   `scenario_configuration_viewer`

-   `scenario_deployment_viewer`

-   `scenario_artifact_viewer`

-   `scenario_execution_viewer`

-   `scenario_metric_viewer`

-   `aicore_credential_viewer`

-   `aicore_connection_viewer`

-   `aicore_resourcegroup_viewer`

-   `aicore_application_viewer`




</td>
</tr>
<tr>
<td valign="top">

`aicore_admin`

</td>
<td valign="top">

-   `scenario_configuration_editor`

-   `scenario_deployment_editor`

-   `scenario_deployment_predictor`

-   `scenario_execution_editor`

-   `scenario_artifact_editor`

-   `aicore_credential_admin`

-   `aicore_connection_admin`

-   `aicore_resourcegroup_editor`

-   `aicore_log_viewer`

-   `aicore_application_admin`




</td>
</tr>
<tr>
<td valign="top">

`aicore_scenario_viewer`

</td>
<td valign="top">

-   `scenario_metadata_viewer`

-   `scenario_executable_viewer`

-   `scenario_configuration_viewer`

-   `scenario_deployment_viewer`

-   `scenario_artifact_viewer`

-   `scenario_execution_viewer`

-   `scenario_metric_viewer`




</td>
</tr>
<tr>
<td valign="top">

`aicore_scenario_editor`

</td>
<td valign="top">

-   `scenario_configuration_editor`

-   `scenario_deployment_editor`

-   `scenario_deployment_predictor`

-   `scenario_execution_editor`

-   `scenario_artifact_editor`




</td>
</tr>
<tr>
<td valign="top">

`aicore_resourcegroup_viewer`

</td>
<td valign="top">

-   `aicore_resourcegroup_viewer`




</td>
</tr>
<tr>
<td valign="top">

`aicore_resourcegroup_editor`

</td>
<td valign="top">

-   `aicore_connection_admin`




</td>
</tr>
<tr>
<td valign="top">

`aicore_application_admin`

</td>
<td valign="top">

-   `aicore_application_admin`




</td>
</tr>
<tr>
<td valign="top">

`aicore_repository_admin`

</td>
<td valign="top">

-   `aicore_repository_admin`




</td>
</tr>
</table>

**Related Information**  


[User Authentication and Administration](user-authentication-and-administration-b0d21d5.md "")

