<!-- loioedb1aa02351349f3adc94a77b631d9bd -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# View an Application

You can investigate details for an application used within your instance of SAP AI Core.



<a name="loioedb1aa02351349f3adc94a77b631d9bd__prereq_jxh_bpc_rob"/>

## Prerequisites

You have the `aicore_admin_applications_viewer` role or a role collection that contains it. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).



## Context

Application details include sync status and health information, source repository, and system messages for any synced resources.



## Procedure

1.  In the *Workspaces* app, choose an AI API connection.

2.  Open the *SAP AI Core Administration* app and choose *Applications*.

    The *Applications* screen appears with a tile for each existing application.

3.  Find the tile for the application you would like to display, and click the tile.

    The *Application Details* screen appears with summary, source, and sync resource details.

    -   Summary details include sync status and health \(returned by the application\), and sync and reconciliation timestamp details

        > ### Note:  
        > To show extra details for the sync or health status choose <span class="SAP-icons-V5"></span> \(Info\).

    -   Source repository details include the name, URL, repository path, and revision

    -   Sync details include resource ID, kind, sync status, and messages for any synced resources

        > ### Note:  
        > Each synced resource is uniquely identified by an ID. This ID is also visible in the *ML Operations* app for the corresponding executable.


    > ### Tip:  
    > If you have the `aicore_admin_applications_editor` role, you can also *Edit* or *Delete* the application from the *Application Details* screen.


