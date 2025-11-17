<!-- loioad7f17d42b80403691fce40373b11286 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Delete an Orchestration Config



## Prerequisites

-   You have either the `genai_manager` or `orchestration_manager` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

-   Users with only the `genai_experimenter` or `orchestration_experimenter` roles are not able to delete orchestration configs. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

-   You've saved an orchestration workflow. For more information, see [Save an Orchestration Config](save-an-orchestration-config-b687c7d.md).

> ### Note:  
> Orchestration configs are saved in one region only and can only be retrieved or deleted by an instance of AI launchpad in that region. 



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app and choose a resource group.

    The *Generative AI Hub* app is now clickable in your side navigation panel and resource groups are listed. 

2.  In the *Generative AI Hub* app, choose *Orchestration*.

    Existing versions of your orchestration configs will be listed.

3.  Select the config and version that you want to delete.

    Select the <span class="SAP-icons-V5">-</span> \(Menu\) icon and choose *Delete* from the drop down list.

    If you have multiple revisions, the current revision will be deleted.

    If you have a single revision, the current version will be deleted.

    If you have a single revision and a single version, the config will be deleted.


