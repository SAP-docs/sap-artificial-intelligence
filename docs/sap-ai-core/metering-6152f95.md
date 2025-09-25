<!-- loio6152f9533f52403e904aa8ba8309a6eb -->

# Metering

Describes how SubaccountID and ServiceInstanceID are available as environment variables in the workflow runtime for metering.

For metering purposes, the workflow runtime automatically injects the following environment variables into each workflow pod:

-   `AICORE_CAS_SUBACCOUNT_ID`: The Subaccount ID of the CaaS consumer.

-   `AICORE_CAS_SERVICE_INSTANCE_ID`: The Service Instance ID of the CaaS consumer.


These environment variables are available to all processes running inside the workflow pod. You can use them to track usage, or integrate with metering system.

In your workflow container, you can access these variables using the following bash script:

```

echo "Subaccount ID: $AICORE_SUBACCOUNT_ID"
echo "Service Instance ID: $AICORE_SERVICE_INSTANCE_ID"
```

