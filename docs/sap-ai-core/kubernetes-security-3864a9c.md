<!-- loio3864a9c5401f4115966a737e4b3a8026 -->

# Kubernetes Security

We recommend that you enable the relevant and applicable Kubernetes security features on your workflow templates and serving templates. Ensure that you enable the appropriate Kubernetes features for your workloads.



<a name="loio3864a9c5401f4115966a737e4b3a8026__section_g3x_srj_3fc"/>

## Restricted Pod Settings

To ensure proper security configurations for containers, certain security-related pod fields must adhere to specific values. There is a large number of pod fields, which change over time. Here, we list the most important fields and their required settings. You do not have to explicitly set these values on your own, however if you set these fields incorrectly, the pod will be rejected.



<a name="loio3864a9c5401f4115966a737e4b3a8026__section_jy1_5rj_3fc"/>

## Setting for `PodSecurityContext`


<table>
<tr>
<th valign="top">

Capability

</th>
<th valign="top">

Setting

</th>
</tr>
<tr>
<td valign="top">

`Add`

</td>
<td valign="top">

Must not be set

</td>
</tr>
<tr>
<td valign="top">

`Drop`

</td>
<td valign="top">

Must contain exactly one element: `['all']`

</td>
</tr>
<tr>
<td valign="top">

`RunAsUser`

</td>
<td valign="top">

Must be set to `65534`

</td>
</tr>
<tr>
<td valign="top">

`RunAsGroup`

</td>
<td valign="top">

Must be set to `65534`

</td>
</tr>
<tr>
<td valign="top">

`RunAsNonRoot`

</td>
<td valign="top">

Must be set to `true`. The pod must run as a non-root user

</td>
</tr>
<tr>
<td valign="top">

`AllowPrivilegeEscalation`

</td>
<td valign="top">

Must be set to `false`

</td>
</tr>
</table>

These settings are enforced internally. If your pod is rejected, it is likely due to one or more of these fields being set incorrectly. Please review your configuration and ensure compliance with the above requirements.

**Related Information**  


[Security Best Practices for Kubernetes Deployment](https://kubernetes.io/blog/2016/08/security-best-practices-kubernetes-deployment/)

