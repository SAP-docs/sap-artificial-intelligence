<!-- loio8cb3c184e26b450dac32790e4f0f3226 -->

# Docker Images

SAP AI Core supports tenant-specific Docker registries \(registered via the administration APIs\). Additional tenant workloads, such as for execution and deployments, can be created by referencing the Docker images from this Docker registry.

Docker images are cached on virtual machines. These cached Docker images cannot be accessed by other tenants and will not be accessed by SAP.

Cached Docker images are not deleted immediately upon tenant offboarding but are cleaned up as part of operational events such as cluster scaling-down behavior, maintenance, and upgrade of virtual machines.

With every service that you consume, there is a shared security responsibility between you and SAP. Because the creation of a Docker image is the responsibility of the tenant, we strongly recommend that you do not embed or hard-code personal data, sensitive data, or machine learning models inside your Docker images.

For security reasons, Docker containers in SAP AI Core are run as non-root only. For more information, see [Workflow Templates](https://help.sap.com/viewer/db13d59d17204c01b3b79c24fb82a19a/CLOUD/en-US/83523ab8b49245bcbc9f1bf0969e32d8.html "Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.") :arrow_upper_right:.

