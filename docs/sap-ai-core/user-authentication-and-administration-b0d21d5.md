<!-- loiob0d21d53c4f0489cb5760cbe3abc40e8 -->

# User Authentication and Administration

SAP AI Core uses the user management and authentication mechanisms provided by SAP Authorization and Trust Management service \(XSUAA\).

For information about SAP Authorization and Trust Management service \(XSUAA\) in SAP BTP, see [What Is the SAP Authorization and Trust Management Service?](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/649961f8d4ad463daca33b3a20deba4c.html)

> ### Note:  
> The data security provisions of SAP AI Core also apply to the SAP AI Core toolkit.
> 
> The SAP AI Core extension persists the connection details of the SAP AI Core engine. The connection details are persisted in an encrypted format in the application memory of the machine from which the user launches Visual Studio Code and installs the SAP AI Core toolkit extension.



<a name="loiob0d21d53c4f0489cb5760cbe3abc40e8__section_crv_mch_ynb"/>

## User Authentication

Authentication in SAP AI Core is based on JSON web tokens \(JWTs\).

For named user communication, obtain a JWT token using password grant OAuth2.0 flow. The user's JWT token contains the scope as defined by the role or role collection assigned \(see [User Roles](user-authentication-and-administration-b0d21d5.md#loiob0d21d53c4f0489cb5760cbe3abc40e8__section_ngw_bv2_3rb)\). Consuming applications must have an application router or REST gateway that accepts the user name and password, and that obtains the user token.

For technical user communication, obtain a JWT token using the client credentials OAuth 2.0 flow.



<a name="loiob0d21d53c4f0489cb5760cbe3abc40e8__section_ngw_bv2_3rb"/>

## User Roles

SAP AI Core provides role templates and role collections that are available under the SAP Authorization and Trust Management service \(XSUAA\). These templates and collections help you to manage and control access to SAP AI Core functionality and resources, such as scenarios, deployments, and executions.

A role template is a collection of scopes, references, and optional attribute references. A role collection is a set of role templates. Your security administrator can assign a role collection to a specific user or to a group of users.

> ### Note:  
> You must have Security Administrator permissions to create users and assign roles.

SAP AI Core supports the user roles outlined in [Roles and Authorizations](roles-and-authorizations-e790986.md).

-   **[Roles and Authorizations](roles-and-authorizations-e790986.md "SAP AI Core
		provides default role collections that you can assign to users. The role collections
		determine which actions a user is able to carry out in SAP AI Core. You can also
		create your own role collections and assign the required roles to them.")**  
SAP AI Core provides default role collections that you can assign to users. The role collections determine which actions a user is able to carry out in SAP AI Core. You can also create your own role collections and assign the required roles to them.

