<!-- loio1945aa4b513c41c9a1fa6dc9301f7b67 -->

# Docker



<a name="loio1945aa4b513c41c9a1fa6dc9301f7b67__section_vjg_yqk_vsb"/>

## Error pulling container main logs. Back-off pulling image

You push a template to SAP AI Core and you get the error ***"Error pulling container main logs". "Back-off pulling image"***.



### Complete the following steps:

1.  Make sure that your Docker Registry is public-facing and not protected behind the firewall of your organization.

    If your Docker Image isn’t public, verify that you have created a Docker Registry secret in SAP AI Core.

2.  Check that you can pull your Docker Image on your local computer using the credentials from the previous step.
3.  Specify the same Docker Registry secret in your executable.
4.  Specify the path to your Docker Image in your executable in following format:

    <code><i class="varname">&lt;DOCKER_REGISTRY&gt;</i>/<i class="varname">&lt;REPO_NAME&gt;</i>/<i class="varname">&lt;DOCKER_IMAGE&gt;</i>:<i class="varname">&lt;TAGNAME&gt;</i></code>

    > ### Example:  
    > `docker.io/tutorialrepo/text-clf-train:0.0.1`


**Parent topic:**[Troubleshooting](troubleshooting-3da90ba.md "For troubleshooting information, see the following sections:")

**Related Information**  


[Repository](repository-fcad603.md "")

[Configuration](configuration-047fad5.md "")

[Artifacts](artifacts-c655daa.md "")

[Application](application-7f1e35b.md "")

[Execution](execution-5ccde4d.md "")

[Deployment](deployment-a10fa8a.md "")

[Miscellaneous](miscellaneous-10622b5.md "")

