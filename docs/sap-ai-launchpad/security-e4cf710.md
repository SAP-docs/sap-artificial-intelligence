<!-- loioe4cf7102c2574e8b85f669b9c4f69cde -->

# Security

Here, we'll explain some of the security aspects of SAP AI Launchpad.

<a name="loiof1d2eb91d9a248ca8c92b0110c76c6f6"/>

<!-- loiof1d2eb91d9a248ca8c92b0110c76c6f6 -->

## Data Protection and Privacy

For general information about data protection and privacy on SAP Business Technology Platform, see [Data Protection and Privacy](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7e513d31704a4a87831191e504ca850a.html).

Data protection is associated with numerous legal requirements and privacy concerns. In addition to compliance with general data protection and privacy acts, it is necessary to consider compliance with industry-specific legislation in different countries. SAP provides specific features and functions to support compliance with regard to relevant legal requirements, including data protection. SAP does not give any advice on whether these features and functions are the best method to support company, industry, regional, or country-specific requirements. Furthermore, this information should not be taken as advice or a recommendation regarding additional features that would be required in specific IT environments. Decisions related to data protection must be made on a case-by-case basis, taking into consideration the given system landscape and the applicable legal requirements.

> ### Note:  
> SAP does not provide legal advice in any form. SAP software supports data protection compliance by providing security features and specific data protection-relevant functions, such as simplified blocking and deletion of personal data. In many cases, compliance with applicable data protection and privacy laws will not be covered by a product feature. Definitions and other terms used in this document are not taken from a particular legal source.

SAP Data Protection and Privacy \(DPP\) requirements and the European Union's General Data Protection Regulations \(GDPR\) mandate the protection of personal and private data at higher standards than other customer data. SAP machine learning services do not import, output, or process any structured personal or private customer data, and cannot distinguish personal or private data from other types of data. Customers are therefore obliged to fulfill the GDPR personal data broker obligations if such data is present.

> ### Caution:  
> Do not store sensitive data in prompts when using the generative AI hub. Sensitive data is any data that is not intended for public disclosure, including but not limited to confidential or personal information.



<a name="loiof1d2eb91d9a248ca8c92b0110c76c6f6__section_w3k_wch_ynb"/>

## Read Access Logging

SAP AI Launchpad stores tenant id \(identity-zone, JWT token's zid\) in application and audit logs, which are sent to the ELK stack and audit log service respectively. SAP Business Technology Platform persists application logs in the ELK log-stash for 7 days.



<a name="loiof1d2eb91d9a248ca8c92b0110c76c6f6__section_yj3_fdh_ynb"/>

## Deletion

The audit log data stored for your account will be retained for 30 days, after which it will be deleted.

For users who are manually offboarded from the generative AI hub data deletion is triggered immediately.

For data deletion resulting from the deletion of a resource group, deletion is triggered within 24 hours.

For data deletion from the generative AI hub resulting from the removal of an SAP AI Core tenant, SAP AI Launchpad connection to SAP AI Core or SAP AI Launchpad instance, data will be retained for 30 days, after which it will be deleted.

> ### Note:  
> User data is saved in one region only and can only be retrieved or deleted by an instance of AI launchpad in that region.

<a name="loioab5939567cf04016854414774fb2291e"/>

<!-- loioab5939567cf04016854414774fb2291e -->

## Security and Customer Data Protection

SAP product standard security and the data protection and privacy \(DPP\) requirements set high standards and obligations when it comes to securing and protecting customer data that is entrusted to SAP.

Customer data protection is handled in three ways:

-   Customer data is imported, output, and processed by the services for no purpose beyond that to which the customer has subscribed.
-   Customer data is protected from malicious access by security technologies that include authentication and authorization.
-   Customer data is protected from accidental exposure to SAP administrators or support persons by security policies, access controls, and monitoring.

<a name="loio42a8f0fd505d4fdca3ed1dc1de14ca07"/>

<!-- loio42a8f0fd505d4fdca3ed1dc1de14ca07 -->

## Encryption in Transit

Communication with the service, including data upload and download, is encrypted using the transport layer security \(TLS\) protocol. SAP services support only the latest protocol versions \(that is, TLS v1.2 and later\) and strong cipher suites. Your systems must use the supported protocol versions and cipher suites to set up secure communication with the services. They must also validate the certificates against the services’ domain names to avoid man-in-the-middle attacks.

<a name="loiodef9ee82675a4cb3a0f718cfc8d940dc"/>

<!-- loiodef9ee82675a4cb3a0f718cfc8d940dc -->

## User Authentication and Authorization

SAP machine learning services use the advanced OAuth 2.0 protocol for authentication and authorization. Customer systems must implement strong protection to safeguard the authentication credentials \(client credentials\).

SAP AI Launchpad uses standard SAP Authorization and Trust Management service services, which lets you manage user authorizations and trust to identity providers.

SAP AI Launchpad integrates with the User Account and Authentication service \(SAP CP XSUAA\). This allows the federation of external and custom identity providers \(IdP\).



<a name="loiodef9ee82675a4cb3a0f718cfc8d940dc__section_crv_mch_ynb"/>

## Configuring External Identity Providers

Information on how to configure external identity providers is available in the SAP Business Technology Platform documentation:

-   For information about the configuration of identity providers via UAA, see [Data Protection and Privacy](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/7e513d31704a4a87831191e504ca850a.html?version=Cloud).
-   For information about establishing trust between UAA and the Identity Authentication service \(IAS\), see [Establish Trust and Federation Between UAA and Identity Authentication](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7c6aa87459764b179aeccadccd4f91f3.html).

The configuration is handled within the security configuration dashboard of the subaccount that contains the relevant instance.

<a name="loiob41f83775fa44cea906961e8124986c5"/>

<!-- loiob41f83775fa44cea906961e8124986c5 -->

## Auditing and Logging Information

Here you can find a list of the security events that are logged by SAP AI Launchpad.

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

Login Successful

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing event details.

</td>
</tr>
<tr>
<td valign="top">

Scope check failed

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “User not authorized” and event details.

</td>
</tr>
<tr>
<td valign="top">

Ops Backend

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Accessing secrets”.

</td>
</tr>
<tr>
<td valign="top">

Scope check failed

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Authorization failed for *<scope\>*”.

</td>
</tr>
<tr>
<td valign="top">

Scope check failed

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Authorization failed for *<scope\>*”.

</td>
</tr>
<tr>
<td valign="top">

Successful onboarding

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Successful onboarding of tenant: *<tenant subdomain\>*”.

</td>
</tr>
<tr>
<td valign="top">

Failed Onboarding

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Failed onboarding of tenant: *<tenant subdomain\>*”.

</td>
</tr>
<tr>
<td valign="top">

Successful Offboarding

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Successful offboarding of tenant: *<tenant subdomain\>*”.

</td>
</tr>
<tr>
<td valign="top">

Failed Offboarding

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Failed offboarding of tenant: *<tenant subdomain\>*”.

</td>
</tr>
<tr>
<td valign="top">

Scope check failed

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing "Authorization failed for <scope\>".

</td>
</tr>
<tr>
<td valign="top">

Read Connections Successful

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing "Read for all connections successful".

</td>
</tr>
<tr>
<td valign="top">

Read Connections Failed

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Failed to read for all connections”.

</td>
</tr>
<tr>
<td valign="top">

Create Connection Successful

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing "Created connection <name\>".

</td>
</tr>
<tr>
<td valign="top">

Create Connection Successful

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing "Failed to create connection <name\>".

</td>
</tr>
<tr>
<td valign="top">

Delete Connection Successful

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Deleted connection *<name\>*”.

</td>
</tr>
<tr>
<td valign="top">

Delete Connection Failed

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; data containing “Failed to delete connection *<name\>*”.

</td>
</tr>
<tr>
<td valign="top">

Modify Connection

</td>
<td valign="top">

Message containing a time stamp, tenant, and user IDs; attributes containing the updated connection properties.

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

