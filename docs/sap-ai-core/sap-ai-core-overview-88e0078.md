<!-- loio88e007863ca545438e274cbf6ce2d7c6 -->

# SAP AI Core Overview

SAP AI Core is the key to integrating artificial intelligence capabilities in your SAP solutions.

Specifically, SAP AI Core helps you to:

-   Seamlessly and easily embed AI capabilities into other applications

-   Leverage high-volumes of data from applications to create robust AI learning models

-   Execute AI training on accelerated hardware

-   Serve AI inference with low latency and high-throughput in a cost-efficient manner

-   Adhere to a compliant, explainable, and maintainable process

-   Manage all stages of the AI lifecycle using a comprehensive set of tools and services

-   Focus on the productization and operationalization of AI scenarios


Management and operations of your AI content \(such as versioning, deployment, and monitoring\) is unified across your SAP solutions. Authoring of your AI content is, however, open to different toolsets \(such as JupyterLab\).

The SAP AI Core service is intended to be used together with SAP AI Launchpad and the `AI API`. The key components are SAP AI Core, SAP AI Launchpad, and the `AI API`.

-   **SAP AI Core** provides an engine that lets you run AI workflows and model serving workloads.

-   **SAP AI Launchpad** manages a number of AI runtimes. It allows various user groups to access and manage their AI scenarios.

-   **AI API** provides a standard way of managing the AI scenario lifecycle on different runtimes, regardless of whether they are provided on SAP technology \(such as SAP S/4HANA\) or on partner technology \(such as Amazon Web Services\). When the AI API is deployed on runtimes other than SAP AI Core, the runtimes have to provide a runtime adapter.


[Figure 1](sap-ai-core-overview-88e0078.md#loio88e007863ca545438e274cbf6ce2d7c6__fig_blw_g1y_xnb) shows these three main components in an overview architecture diagram.

  
  
**Overview Architecture**

![Overview of the AI Core landscape](images/Image_AI_Core_Overview_8a6312d.png)

**Parent topic:**[Concepts](concepts-4c6b2da.md "In this section, we'll explore some of the concepts surrounding SAP AI Core.")

**Related Information**  


[Overview of SAP AI Core Systems](overview-of-sap-ai-core-systems-c243d2a.md "Your SAP AI Core system connects internal and external tools.")

[Terminology](terminology-05f41ee.md "")

[Resource Groups](resource-groups-26c6c6b.md#loio26c6c6b50e3f412f8bc0cd6a8ebdb850 "SAP AI Core tenants use resource groups to isolate related ML resources and workloads. Scenarios, executables, and Docker registry secrets are shared across all resource groups.")

