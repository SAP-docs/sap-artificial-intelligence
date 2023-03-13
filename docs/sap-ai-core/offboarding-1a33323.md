<!-- loio1a3332379ca34cf7aefd076ffa621fe7 -->

# Offboarding

To prevent accidental deletion of the service, service providers must provide a deletion strategy as follows:

```

metadata:
	name: sample-service
	annotations: 
		ai.sap.com/serviceDeletionStrategy: "delete"

```

With the codeph strategy annotation, service providers can delete service custom resources from the git repository and proceed for offboarding. For successful service offboarding, all the consumer service instances should be deleted.

