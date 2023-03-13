<!-- loioa2a95a064e5b48db8d5abc7847067a9f -->

# Custom Access for Support User

An SAP Support user may provide troubleshooting support in case of issues in your production environment.



<a name="loioa2a95a064e5b48db8d5abc7847067a9f__context_fnj_qsm_brb"/>

## Context

At some point, you may need to create an incident for an issue that you encounter with SAP AI Launchpad. To investigate the issue, an SAP Support user may require access to your production environment.

SAP Support users access your production environment via an internal user and access management tool called Cloud Access Manager \(CAM\). CAM, much like the SAP ID Service, allows for the packaging of variable levels of access to your production environment in a single requestable profile. The access request is reviewed by a set of named approvers and either approved or rejected. The profiles also define a time period for which access is granted. CAM will automatically revoke access once the time period has elapsed. Users may request access again, but this will once again require review and approval.

On approval, the SAP support user will be able to access your SAP AI Launchpad instance and provide administrative or operations support.

To provide an SAP Support user with custom access to your connections, see [Custom Access for Connections](custom-access-for-connections-8ba6a92.md).

**Related Information**  


[User Authentication and Authorization](security-e4cf710.md#loiodef9ee82675a4cb3a0f718cfc8d940dc "SAP machine learning services use the advanced OAuth 2.0 protocol for authentication and authorization. Customer systems must implement strong protection to safeguard the authentication credentials (client credentials).")

