<!-- loiod1cd77fb7da34eacb0fdece7e5262069 -->

# AI Content Security

AI content covers workflow templates and serving templates, as well as the Docker images used in them. Docker images contain the machine-learning algorithms or code, along with the machine-learning libraries, frameworks, and other dependent packages. Ensure that you follow standard practices for developing secure software when working with AI content.

**Security Practices**


<table>
<tr>
<th valign="top">

Practice

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Threat Modeling

</td>
<td valign="top">

Hold threat modeling workshops to identify and assess security risks or threats in the AI content.

</td>
</tr>
<tr>
<td valign="top">

Static Code Scans

</td>
<td valign="top">

Use static code scan \(SAST\) tools to scan and analyze the code for vulnerabilities.

</td>
</tr>
<tr>
<td valign="top">

Open-Source Vulnerability Scan

</td>
<td valign="top">

Scan any open-source components used by the product for vulnerabilities, and patch any vulnerable OSS components found.

</td>
</tr>
<tr>
<td valign="top">

Open-Source Strategy

</td>
<td valign="top">

Develop an update strategy that defines when the open-source components used in a product or service are updated to the latest secure version.

</td>
</tr>
<tr>
<td valign="top">

Code Reviews

</td>
<td valign="top">

Perform peer code reviews of each code change. The reviewer should take a closer look at the code from a security perspective.

</td>
</tr>
<tr>
<td valign="top">

Malware Scanning

</td>
<td valign="top">

Scan for malware in the data uploaded for AI content.

</td>
</tr>
<tr>
<td valign="top">

Secure Code Protection

</td>
<td valign="top">

Support security assurance starting with source code through deployed service. For example, use Docker image digest and image sign verifications.

</td>
</tr>
<tr>
<td valign="top">

Docker Base Image Security

</td>
<td valign="top">

Use a secure, light base image for building the Docker images for the AI content. Ensure you use the latest available base image and remove unused components from the Docker image.

</td>
</tr>
</table>

