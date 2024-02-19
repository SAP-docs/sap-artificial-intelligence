<!-- loio555c83b997db49ae9f3c302b60bf4062 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Manage a Connection

As an administrator, you can delete, update, or refresh a connection using the *Workspaces* app.



<a name="loio555c83b997db49ae9f3c302b60bf4062__prereq_jxh_cq2_rpb"/>

## Prerequisites

You have the `connections_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).

<a name="loio79c1de643cd5478194cae46505e84026"/>

<!-- loio79c1de643cd5478194cae46505e84026 -->

## Edit a Connection



<a name="loio79c1de643cd5478194cae46505e84026__steps_rcz_gp4_rrb"/>

## Procedure

1.  In the *Workspaces* app, find the connection.

    Each connection appears as a tile. You can search the connections by entering the name or part of the name in the :mag: field.

2.  Select the connection and choose *Edit* to edit the connection's details.

    The *Update AI API Connection* dialog box appears.

3.  Change the connection details as required.

    > ### Tip:  
    > You can't change a connection name once it has been created, However, you can delete the connection \(no data is lost\) and add a new connection to the same runtime instance with a new name. See [Delete a Connection](manage-a-connection-555c83b.md#loiofc28f574020a466e8b03b8805055eb79).
    > 
    > Sensitive fields are masked and entries are not shown in clear text. To ensure these entries are accurate, copy and paste the values from your service key.

    -   You can upload the service key file for your SAP AI Core instance, if available.

        To upload the service key as a `.TXT` or `JSON` file, choose <span class="SAP-icons-V5"></span> \(Upload\) . Search for and choose the local service key file.

        Service key data then defaults to the remaining fields.


4.  Choose *Update*.




<a name="loio79c1de643cd5478194cae46505e84026__result_hyt_gwm_5nb"/>

## Results

The updated connection appears in the *Workspaces* app.

To manage repositories, applications, and docker registry secrets for the connection, see [Administration](administration-cb4dd1e.md).

<a name="loiofc28f574020a466e8b03b8805055eb79"/>

<!-- loiofc28f574020a466e8b03b8805055eb79 -->

## Delete a Connection



<a name="loiofc28f574020a466e8b03b8805055eb79__steps_ty2_5p4_rrb"/>

## Procedure

1.  In the *Workspaces* app, find the connection.

    Each connection appears as a tile. You can search the connections by entering the name or part of the name in the :mag: field.

2.  Select the connection and choose *Delete* to remove the connection from SAP AI Launchpad.

    > ### Note:  
    > No data is lost from your runtime instance to which the connection points. You can add a connection again later.




<a name="loiofc28f574020a466e8b03b8805055eb79__result_hyt_gwm_5nb"/>

## Results

The connection no longer appears in the *Workspaces* app.

