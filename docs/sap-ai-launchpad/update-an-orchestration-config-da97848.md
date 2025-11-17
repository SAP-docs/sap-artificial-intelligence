<!-- loioda978484134b4d8c82dcaad229fdf087 -->

# Update an Orchestration Config



## Prerequisites

-   You have either the `genai_manager` or `orchestration_manager` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

-   Users with only the `genai_experimenter` or `orchestration_experimenter` roles are not able to save orchestration configs. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).

-   You've saved an orchestration workflow. For more information, see [Save an Orchestration Config](save-an-orchestration-config-b687c7d.md).

> ### Note:  
> Orchestration configs are saved in one region only and can only be retrieved or deleted by an instance of AI launchpad in that region. 



## Procedure

1.  Select the connection to your SAP AI Core runtime in the *Workspaces* app and choose a resource group.

    The *Generative AI Hub* app is now clickable in your side navigation panel and resource groups are listed. 

2.  In the *Generative AI Hub* app, choose *Orchestration*.

    Existing versions of your orchestration configs will be listed.

3.  Select the config and version that you want to update, and make your changes.




## Next Steps

You can save your progress by choosing the *Save* button. This will save a new revision. Your revisions will be visible in the *Revisons* panel.

You can save a new version by pressing the arrow on the *Save* button and selecting *Save New Version*. You can use the automated version number, or enter your own in SemVer format. For more information, see [Save an Orchestration Config](save-an-orchestration-config-b687c7d.md).

You can save a new version by choosing the *Save* button and changing the config details. For more information, see [Save an Orchestration Config](save-an-orchestration-config-b687c7d.md).

You can test your new config. For more information, see [Test Your Orchestration Workflow](test-your-orchestration-workflow-5b0183d.md).

