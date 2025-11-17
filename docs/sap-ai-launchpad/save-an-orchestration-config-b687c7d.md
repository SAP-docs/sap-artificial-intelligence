<!-- loiob687c7dacecf49a8bf18c6632de8a627 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Save an Orchestration Config



## Prerequisites

-   You have either the `genai_manager` or `orchestration_manager` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

-   Users with only the `genai_experimenter` or `orchestration_experimenter` roles are not able to save orchestration configs. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

-   You've built your orchestration workflow. For more information, see [Build Your Orchestration Workflow](build-your-orchestration-workflow-b7dc8b4.md) and [Test Your Orchestration Workflow](test-your-orchestration-workflow-5b0183d.md).



## Context

After preparing your orchestration workflow in the *Orchestration* app, you can save it as an orchestration config for later use. You can then continue to update and refine your workflow, incorporate versioning, and manage the lifecycle of your orchestration configs.

> ### Note:  
> Orchestration configs are saved in one region only and can only be retrieved or deleted by an instance of AI launchpad in that region. 



## Procedure



### Saving a New Orchestration Config

You can save a new config by pressing *Save*.

A wizard will open.

-   Provide a name for your config.

-   Choose an existing scenario from the drop down list or enter a new one.


**Results**

Your orchestration config is saved, and a version number has been automatically be applied.



### Saving a New Orchestration Config Version

You can save a new config version by pressing the <span class="SAP-icons-V5"></span> \(Arrow\) icon on the *Save* button and selecting *Save New Version*.

A wizard will open.

You can use the automated versioning, or provide a new version number in SemVer format.

**Results**

Your orchestration config version is saved.



## Next Steps

You can view your existing configs. For more information, see [View Orchestration Configs](view-orchestration-configs-cafd530.md).

You can update your existing configs. For more information, see [Update an Orchestration Config](update-an-orchestration-config-da97848.md).

You can delete a revision, version or config. For more information, see [Delete an Orchestration Config](delete-an-orchestration-config-ad7f17d.md).

