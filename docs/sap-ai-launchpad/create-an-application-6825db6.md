<!-- loio6825db6930ce4da6a1aa2e9e965a32c4 -->

# Create an Application

As a system administrator, you create applications which sync with Git repositories used in your AI processes.



<a name="loio6825db6930ce4da6a1aa2e9e965a32c4__prereq_jxh_bpc_rob"/>

## Prerequisites

You have the `aicore_admin_applications_editor` role or a role collection that contains it. For more information, see [Roles and Authorizations](roles-and-authorizations-4ef8499.md).

The source Git repository required for the application has been added. See [Add a Git Repository](add-a-git-repository-c8cd251.md).



## Procedure

1.  In the *Workspaces* app, choose the AI API connection.

2.  Open the *SAP AI Core Administration* app and choose *Applications*.

    The *Applications* screen appears with a tile for each existing application.

3.  Choose *Create* to create reference details for a new application.

4.  Complete the fields in the *Create a new Application* dialog box as follows:

    1.  Enter an application name.

    2.  Select a source Git repository.

    3.  Enter a path in the repository. The path is used to differentiate between folders within the repository.

    4.  Enter a revision value to indicate the specific branch or tag in the repository. For example, ***HEAD***.


5.  Choose *Create* to create the application for the selected repository.

    The *Applications* screen appears with the new application.




<a name="loio6825db6930ce4da6a1aa2e9e965a32c4__result_trn_hbr_1tb"/>

## Results

The new application is created.

> ### Note:  
> The timing for the initial synchronization is determined by the sync policy for the application.

**Related Information**  


[Create an Application to Sync your Folders](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/fd1aa517b21e495caa691259da38a5d0.html)

