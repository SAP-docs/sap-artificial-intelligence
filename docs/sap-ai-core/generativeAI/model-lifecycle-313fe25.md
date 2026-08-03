<!-- loio313fe258c6b8471eaf10dcb5e09bb07f -->

# Model Lifecycle

Model versions have deprecation dates. Where a model version is specified in a deployment, the deployment stops working on the deprecation date of that model version.

Implement one of the following model upgrade options:

-   **Auto Upgrade:** Create a generative AI configuration and deployment or patch a deployment with a new configuration, specifying `modelVersion` `latest`. When a new `modelVersion` is supported by SAP AI Core, existing generative AI deployments will automatically use the latest version of the given model.

-   **Manual Upgrade:** Create a generative AI configuration with your chosen replacement `modelVersion` and use it to patch your deployment. This model version is used in generative AI deployments irrespective of updates to the models supported by SAP AI Core.

    > ### Note:  
    > If `modelVersion` isn’t specified, it will be `latest` by default. To upgrade manually, you **must** specify a `modelVersion`.


