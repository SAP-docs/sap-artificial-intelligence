<!-- loio684579369a5146a7be8f46a2bf1e8ff7 -->

# Consume mTLS Certificate Secrets

You can consume mTLS certificate secrets in your workloads to authenticate securely with external services that require mutual TLS.

The `mTLS` certificate secrets can be mounted as volumes in your execution or deployment containers. The secret provides a certificate and private key in PEM format. Your workload uses these files to send mTLS-authenticated requests to external services.

> ### Note:  
> `mTLS` certificate secrets can only be consumed as volume mounts. You can't use them as environment variables.



## Mount an mTLS Certificate Secret as a Volume

To mount the certificate and key files in your workload container, define a volume referencing the secret and a corresponding volume mount in your workflow or serving template.

The secret contains two data keys:

-   `tls.crt`— the PEM-encoded X.509 client certificate
-   `tls.key` — the PEM-encoded private key

You can project these keys to custom file paths by using the `items` field.

**Example workflow template:**

```

apiVersion: argoproj.io/v1alpha1
kind: WorkflowTemplate
metadata:
  name: my-mtls-workflow
  annotations:
    scenarios.ai.sap.com/name: "my-scenario"
    executables.ai.sap.com/name: "my-executable"
spec:
  entrypoint: main
  templates:
    - name: main
      inputs:
        parameters:
          - name: mtlsSecretName
      volumes:
        - name: mtls-cert-volume
          secret:
            secretName: "{{inputs.parameters.mtlsSecretName}}"
            items:
              - key: tls.crt
                path: client.crt
              - key: tls.key
                path: client.key
      container:
        image: my-image:latest
        volumeMounts:
          - name: mtls-cert-volume
            mountPath: /mnt/mtls
            readOnly: true
```

Inside the container, the following files are available:

-   `/mnt/mtls/client.crt` — the client certificate
-   `/mnt/mtls/client.key` — the private key

Your application can use these files to configure an mTLS-authenticated HTTP client. For example, in Python:

```

import requests
response = requests.get(
    "https://external-service.example.com/api/data",
    cert=("/mnt/mtls/client.crt", "/mnt/mtls/client.key")
)
      
```



## Parameterize the Secret Name

You can parameterize the secret name so that it's provided during execution creation instead of being hardcoded. Use the `inputs.parameters` mechanism:

```

inputs:
  parameters:
    - name: mtlsSecretName
      
```

When creating the execution through the AI API, provide the parameter value:

```

{
    "parameterBindings": [
        {
            "key": "mtlsSecretName",
            "value": "my-mtls-cert"
        }
    ]
}
      
```



## Additional Information

-   Only `mTLS` certificate secrets that belong to the same resource group as the execution or deployment can be mounted. The platform validates this during admission.
-   If the referenced secret doesn't exist or doesn't belong to the same resource group, the workload is rejected.
-   After certificate rotation, see [Rotate an mTLS Certificate Secret](rotate-an-mtls-certificate-secret-e427cc3.md), the mounted files update automatically. If your application caches the certificate in memory, you must restart the workload to use the new certificate.

