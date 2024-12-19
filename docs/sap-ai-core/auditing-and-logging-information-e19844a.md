<!-- loioe19844a7724f4ec2b6bcc4002f3fd95c -->

# Auditing and Logging Information

Here you can find a list of the security events that are logged by SAP AI Core.

**Security Events Written in Audit Logs**


<table>
<tr>
<th valign="top">

What Events Are Logged

</th>
<th valign="top">

How to Identify Related Log Events

</th>
</tr>
<tr>
<td valign="top">

Creation of object store secret

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Deletion of object store secret

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Successful retrieval of object store secret

</td>
<td valign="top">

Successfully read object store connection details for resource group *<resource group name\>* and object store *<object store name\>* 

</td>
</tr>
<tr>
<td valign="top">

Provisioning of resource group

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Deprovisioning of resource group

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Creation of docker registry secret

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Deletion of docker registry secret

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Creation of deployments

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Deletion of deployments

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Creation of executions

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Deletion of executions

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Creation of ArgoCD application

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Deletion of ArgoCD application

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Creation of repositories

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Deletion of repositories

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing the API call and `"new": "Succeeded"`.

</td>
</tr>
<tr>
<td valign="top">

Provisioning of tenant

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing `"name": "state",`, `"new": "PENDING"` and `"name": "cfAccountState`, `"new": "ACTIVE"` and success value `true` 

</td>
</tr>
<tr>
<td valign="top">

Retrieval of tenant

</td>
<td valign="top">

Message containing `Attribute <attribute detail> was read`.

</td>
</tr>
<tr>
<td valign="top">

Deprovisioning of tenant

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, and attributes containing `"name": "state",`, `"new": "PENDING"` and `"name": "cfAccountState`, `"new": "DELETED"` and success value `true`.

</td>
</tr>
<tr>
<td valign="top">

-   List
-   Get
-   Watch



</td>
<td valign="top">

Message containing a time stamp, tenant IDs, source IPs, the request URI, and the level.

</td>
</tr>
<tr>
<td valign="top">

-   Create
-   Update
-   Patch



</td>
<td valign="top">

Message containing a time stamp, tenant IDs, source IPs, the request URI, the level, and the request and response objects.

</td>
</tr>
<tr>
<td valign="top">

Delete

</td>
<td valign="top">

Message containing a time stamp, tenant IDs, source IPs, the request URI, the level, the and response object.

</td>
</tr>
<tr>
<td valign="top">

Token expired

</td>
<td valign="top">

***Jwt is expired*** 

</td>
</tr>
<tr>
<td valign="top">

No authorization header

</td>
<td valign="top">

***RBAC: access denied*** 

</td>
</tr>
<tr>
<td valign="top">

Invalid token

</td>
<td valign="top">

***Jwt issuer is not configured*** 

</td>
</tr>
<tr>
<td valign="top">

Wrong `tenantId` 

</td>
<td valign="top">

***Jwt verification fails*** 

</td>
</tr>
</table>



The following information is described in the table columns:

-   *Event grouping* - Events that are logged with a similar format or are related to the same entities.

-   *What events are logged* - Description of the security or data protection and privacy related event that is logged.

-   *How to identify related log events* - Search criteria or key words, that are specific for a log event that is created along with the logged event.

-   *Additional information* - Any related information that can be helpful.


**Related Information**  


[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html)

[Audit Logging in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/02c39712c1064c96b37c1ea5bc9420dc.html)

