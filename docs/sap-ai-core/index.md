# SAP AI Core

-   [What Is SAP AI Core?](what-is-sap-ai-core-d029a32.md)
-   [What's New for SAP AI Core](what-s-new-for-sap-ai-core-b7f76ad.md)
    -   [2021 What's New for SAP AI Core \(Archive\)](2021-what-s-new-for-sap-ai-core-archive-797b1f7.md)
-   [Concepts](concepts-4c6b2da.md)
    -   [SAP AI Core Overview](sap-ai-core-overview-88e0078.md)
    -   [Overview of SAP AI Core Systems](overview-of-sap-ai-core-systems-c243d2a.md)
    -   [Terminology](terminology-05f41ee.md)
    -   [Resource Groups](resource-groups-26c6c6b.md#loio26c6c6b50e3f412f8bc0cd6a8ebdb850)
        -   [Scope of Resources](resource-groups-26c6c6b.md#loioc9518c0d0ec44e2e9f767089028ff48c)
-   [Service Plans](service-plans-c7244c6.md)
    -   [Free Tier](free-tier-4533adc.md)
    -   [Metering and Pricing](metering-and-pricing-b5c7215.md)
    -   [Choose a Resource Plan](choose-a-resource-plan-3a06d84.md)
    -   [Update from Free Tier to Standard Plan](update-from-free-tier-to-standard-plan-924f892.md)
-   [About the AI API](about-the-ai-api-716d4c3.md)
-   [Initial Setup](initial-setup-38c4599.md)
    -   [Create a Subaccount](create-a-subaccount-3e3ae83.md)
    -   [Enable Cloud Foundry](enable-cloud-foundry-cf0d5d2.md)
    -   [Create a Space](create-a-space-4c1190c.md)
    -   [Add a Service Plan](add-a-service-plan-86002d9.md)
    -   [Create a Service Instance](create-a-service-instance-34761f9.md)
    -   [Create a Service Key](create-a-service-key-7323ff4.md)
    -   [SAP AI Core Starter Tutorials](sap-ai-core-starter-tutorials-9795b63.md)
-   [ML Operations](ml-operations-7f5aa9b.md)
    -   [Administration](administration-7937fc1.md)
        -   [Manage Your Git Repository](manage-your-git-repository-2cd2996.md)
            -   [Register Your Git Repository and Secrets](register-your-git-repository-and-secrets-b668176.md)
            -   [Create an Application to Sync Your Folders](create-an-application-to-sync-your-folders-80dbecf.md)
        -   [Manage Resource Groups](manage-resource-groups-8aae6cb.md)
            -   [Create a Resource Group](create-a-resource-group-01753f4.md)
            -   [Create a Generic Secret](create-a-generic-secret-1831845.md)
            -   [List All Generic Secrets](list-all-generic-secrets-05a3713.md)
            -   [Update a Generic Secret](update-a-generic-secret-b5d5970.md)
            -   [Delete a Generic Secret](delete-a-generic-secret-d5d5187.md)
            -   [Consume Generic Secrets in Executions or Deployments](consume-generic-secrets-in-executions-or-deployments-185a324.md)
        -   [Manage Object Store Secrets](manage-object-store-secrets-f10b532.md)
            -   [Register Your Object Store Secret](register-your-object-store-secret-b083d73.md)
        -   [Manage Docker Registry Secrets](manage-docker-registry-secrets-c5445c4.md)
            -   [Register Your Docker Registry Secret](register-your-docker-registry-secret-a7cf5e1.md)
    -   [Connect Your Data](connect-your-data-9508bdb.md)
        -   [Manage Artifacts](manage-artifacts-386ba71.md)
            -   [Create Artifacts](create-artifacts-66413f1.md)
            -   [List Artifacts](list-artifacts-1d613e0.md)
    -   [Train Your Model](train-your-model-a9ceb06.md)
        -   [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md)
        -   [Workflow Templates](workflow-templates-83523ab.md)
        -   [List Scenarios](list-scenarios-deedde5.md)
        -   [List Executables](list-executables-80895a4.md)
        -   [Create Configurations](create-configurations-884ae34.md)
        -   [List Configurations](list-configurations-8074b2a.md)
        -   [Start Training](start-training-54b44e4.md)
        -   [Stop Training Instances](stop-training-instances-3d85344.md#loio3d853443027449d9a33723165b19b25a)
            -   [Stop a Single Training Instance](stop-training-instances-3d85344.md#loio07870dfc89fe4218baeda95e994936da)
            -   [Stop Multiple Training Instances](stop-training-instances-3d85344.md#loio09b4810ad29445d19025836ed1ac5151)
        -   [Delete Training Instances](delete-training-instances-612ce17.md#loio612ce172e609432a840a22eb211ecf7b)
            -   [Delete a Single Training Instance](delete-training-instances-612ce17.md#loiodd71f165135f49a194e131fa4ca9d5d3)
            -   [Delete Multiple Training Instances](delete-training-instances-612ce17.md#loioc1c3cc3e3f88417ba785ab8e29564e82)
        -   [Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md)
        -   [Training Schedules](training-schedules-2b702f8.md)
            -   [Create a Training Schedule](create-a-training-schedule-bd409a9.md)
            -   [List Executions Created by a Training Schedule](list-executions-created-by-a-training-schedule-2c1ecfb.md)
            -   [Change an Exisitng Training Schedule](change-an-exisitng-training-schedule-18caf4b.md)
            -   [Delete a Training Schedule](delete-a-training-schedule-9dc25e1.md)
    -   [Use Your Model](use-your-model-7f93e8f.md)
        -   [Choose a Resource Plan](choose-a-resource-plan-8deca74.md)
        -   [Serving Templates](serving-templates-20a8667.md)
            -   [Serving Template API Reference](serving-template-api-reference-51b2271.md)
                -   [API Schema Spec ai.sap.com/v1alpha1](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md)
                -   [KServe Spec serving.kserve.io/v1beta1](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md)
            -   [Change Serving Template and Update Deployments](change-serving-template-and-update-deployments-9555fe1.md)
        -   [List Executables](list-executables-6af8e60.md)
        -   [Deploy Models](deploy-models-dd16e8e.md)
        -   [Inference](inference-e348ecf.md)
        -   [Update a Deployment](update-a-deployment-9789ddd.md)
        -   [Stop Deployments](stop-deployments-b7d2577.md#loiob7d2577088c84417bbab370173d38cd8)
            -   [Stop a Single Deployment](stop-deployments-b7d2577.md#loio1fa895527bd64c6c878733e293da99dc)
            -   [Stop Multiple Deployments](stop-deployments-b7d2577.md#loio331cdf505d1c47618256a83920dd7c9a)
        -   [Delete Deployments](delete-deployments-0193d17.md#loio0193d17a7bdb4ae08a9c8301d1d8c1b8)
            -   [Delete a Single Deployment](delete-deployments-0193d17.md#loio1b0b3612e5f948a6af5e593a61f711ce)
            -   [Delete Multiple Deployments](delete-deployments-0193d17.md#loio6b521aa3dfa1465a9be658bdb38fb2e5)
        -   [Efficiency Features](efficiency-features-9fad26a.md)
        -   [Retrieve Deployment Logs](retrieve-deployment-logs-4c86b88.md)
    -   [Metrics](metrics-36f8bec.md)
        -   [Tracking](tracking-c059e0f.md)
            -   [Metrics Tracking with AI API](metrics-tracking-with-ai-api-9a335bd.md)
                -   [Get Metrics](get-metrics-44d73d4.md)
                -   [Query Metric Data](query-metric-data-f25046f.md)
                -   [Store Metric Data](store-metric-data-ab04f04.md)
                -   [Delete Metrics](delete-metrics-1474d43.md)
-   [Advanced Features](advanced-features-24f2fbb.md)
    -   [AI Content as a Service](ai-content-as-a-service-3fb0390.md)
        -   [Service Custom Resource](service-custom-resource-59f767c.md)
        -   [Onboarding](onboarding-50a6d9f.md)
        -   [Offboarding](offboarding-1a33323.md)
-   [Libraries and SDKs](libraries-and-sdks-499309d.md)
-   [Tutorials](tutorials-a5c80a6.md)
-   [Security](security-a476d3c.md#loioa476d3c15bf04494907dcdb7a9aee131)
    -   [Data Protection and Privacy](security-a476d3c.md#loiod25e4c9f12554f2c982ea4f59b04f625)
        -   [Data Storage and Processing](security-a476d3c.md#loio74fc987a6e704cd0b753e3c12f6a7d1f)
        -   [Change Logging and Read-Access Logging](security-a476d3c.md#loio7cf145520b924a6c8dc7461265025a98)
        -   [Consent](security-a476d3c.md#loio9fc8fcbd5a64405490307233877d8779)
        -   [Deletion](security-a476d3c.md#loio44d7acf7ebe3406cbe457388cca97e86)
        -   [Security and Customer Data Protection](security-a476d3c.md#loioab5939567cf04016854414774fb2291e)
    -   [Security in SAP AI Core](security-a476d3c.md#loio226b593aa7e64a538281bbb7489912ab)
        -   [Security Features of Data, Data Flow and Processes](security-a476d3c.md#loio893936c084114e3591c5c4b36b1d0cc5)
        -   [Encryption in Transit](security-a476d3c.md#loio42a8f0fd505d4fdca3ed1dc1de14ca07)
        -   [User Authentication and Administration](security-a476d3c.md#loiob0d21d53c4f0489cb5760cbe3abc40e8)
            -   [Roles and Authorizations](security-a476d3c.md#loioe7909866a6294b4ab9974dcebc8336f4)
        -   [Docker Images](security-a476d3c.md#loio8cb3c184e26b450dac32790e4f0f3226)
        -   [AI Content Security](security-a476d3c.md#loiod1cd77fb7da34eacb0fdece7e5262069)
        -   [Kubernetes Security](security-a476d3c.md#loio3864a9c5401f4115966a737e4b3a8026)
        -   [Output Encoding](security-a476d3c.md#loio2b4c76d85b614dcc931bbe55902f6d6a)
    -   [Multitenancy](security-a476d3c.md#loioee90fe114c26439fb0feff9f8f014458)
        -   [Tenant Level Resources](security-a476d3c.md#loio9cc1a9d437f54c3c8feb769994a27d25)
        -   [Resource Group Level Resources](security-a476d3c.md#loiofbfa1badbbfa4981a417299238b82e39)
-   [Accessibility Features in SAP AI Core](accessibility-features-in-sap-ai-core-8abff75.md)
-   [Monitoring and Troubleshooting](monitoring-and-troubleshooting-f559038.md)
    -   [Troubleshooting](troubleshooting-3da90ba.md)
        -   [Repository](repository-fcad603.md)
        -   [Configuration](configuration-047fad5.md)
        -   [Artifacts](artifacts-c655daa.md)
        -   [Application](application-7f1e35b.md)
        -   [Execution](execution-5ccde4d.md)
        -   [Docker](docker-1945aa4.md)
        -   [Deployment](deployment-a10fa8a.md)
        -   [Miscellaneous](miscellaneous-10622b5.md)
-   [Service Offboarding](service-offboarding-08303fe.md)
