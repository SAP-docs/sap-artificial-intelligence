<!-- loio893936c084114e3591c5c4b36b1d0cc5 -->

# Security Features of Data, Data Flow, and Processes

The table below shows an overview of the data flow for SAP AI Core.

**Overview of Data and Security Measures**


<table>
<tr>
<th valign="top">

Step

</th>
<th valign="top">

Description

</th>
<th valign="top">

Security Measure

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

Transmission control/communication security

</td>
<td valign="top">

Encrypted \(HTTPS\) communication. Data-in-transit is encrypted using state-of-the-art TLS settings.

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

Application data residing in persistence layer

</td>
<td valign="top">

Encrypted at rest with state-of-the-art encryption keys generated and maintained by SAP.

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

Application data residing in persistence layer

</td>
<td valign="top">

Backup and restore capabilities are implemented and tested regularly. Backups are stored in remote locations and backups are encrypted at rest with state-of-the-art encryption keys generated and maintained by SAP.

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

Access control and separation by purpose

</td>
<td valign="top">

Roles and scopes are available for implementing access control. Customer admin can use standard BTP security administration capabilities to assign roles to users to ensure “least privilege” and “segregation of duties”.

</td>
</tr>
</table>

