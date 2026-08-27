<!-- loio2f02a1d6e3974464a4dcf7bd85fcdcac -->

# Using Artifact Signatures

Artifact signatures in the form of a hash can be added to output artifacts from executions.



<a name="loio2f02a1d6e3974464a4dcf7bd85fcdcac__section_g1c_zfd_2yb"/>

## Providing Signatures for Output Artifacts

A hash is an identifier that is generated using the file contents. Hashes can therefore be used to compare two files and verify the integrity of a file. SAP AI Core doesn’t create or verify the signatures, but stores them and makes them available. Artifact signatures are created and stored with the artifact.

To provide a signature for an output artifact, specify the `AICORE_ARTIFACT_SIGNATURES` output parameter in the workflow template. For more information, see [Argo Workflows Output Parameters](https://argoproj.github.io/argo-workflows/walk-through/output-parameters/). This parameter specifies a path to a file that will contain the signatures as key-value-pairs in JSON format.

```
apiVersion: argoproj.io/v1alpha1
kind: WorkflowTemplate
metadata:
  name: signature-example
  annotations:
    scenarios.ai.sap.com/description: "Example for signature feature"
    scenarios.ai.sap.com/name: "signature-example-scenario"
    executables.ai.sap.com/description: "Output artifact example for signature feature"
    executables.ai.sap.com/name: "signature-example-output-artifacts"
  labels:
    scenarios.ai.sap.com/id: "signature-example-scenario"
    executables.ai.sap.com/id: "signature-example-out-art"
    ai.sap.com/version: "1.0.0"
spec:
  entrypoint: output-artifact-signatures-example
  templates:
    - name: output-artifact-signatures-example
      outputs:
        # specify an output artifact named "dummy-model"
        artifacts:
          - name: dummy-model
            path: /tmp/model
            globalName: dummy-model
        # specify an output parameter with name 'AICORE_ARTIFACT_SIGNATURES'
        # this parameter should point to a file in valid JSON format, containing an object with key-value pairs, where each key is
        # the globalName of an output artifact and the value is its signature
        parameters:
          - name: AICORE_ARTIFACT_SIGNATURES  # the parameter name has to be exactly 'AICORE_ARTIFACT_SIGNATURES'
            valueFrom:
                path: /tmp/signatures.json  # the value of the path can be set arbitrary
      container:
        image: python:3.11-alpine
        imagePullPolicy: Always
        command: ["python", "-c"]
        args: 
            - |
              import hashlib, json
              model = "a dummy string serving as output artifact"
              model_signature = hashlib.sha256(model.encode("utf-8")).hexdigest()  # create a hash of the dummy model 
              signatures = {
                  # the key is the globalName of the output artifact, the value is its signature
                  "dummy-model": model_signature 
              }
              # write the dummy model to disk
              with open("/tmp/model", "w") as f:
                  f.write(model)
              # write the model signatures dictionary to the path specified in the AICORE_ARTIFACT_SIGNATURES output parameter
              with open("/tmp/signatures.json", "w") as f:
                  json.dump(signatures, f)
              print("success")
```

The example template can be used with multiple output artifacts. For each artifact, you add another entry in the signatures object.

The template produces the output artifact ***dummy-model***, with its name-signature key-value pair provided in the `AICORE_ARTIFACT_SIGNATURES` output parameter. The key is the global name of the output artifact, and the value is the signature. For example:

```
{
  "name-of-model1": "signature-of-model1"
}
```

These signatures can then be consumed in another execution.

> ### Note:  
> Signatures must be generated as part of the training workflow, and can’t be added retrospectively.

> ### Note:  
> When you query the execution via the GET `{{apiurl}}/v2/lm/executions/{{executionid}}` endpoint you won’t see the signatures of the output artifacts, as they’re kept internally. However, you’ll still be able to use them in other executions or deployments.



<a name="loio2f02a1d6e3974464a4dcf7bd85fcdcac__section_nzw_hgd_2yb"/>

## Multi-Step Workflows

For multistep workflow templates, the `AICORE_ARTIFACT_SIGNATURES` output parameter needs to be supplied in each step that requires an output artifact and signature to be created. See the following example:

```
apiVersion: argoproj.io/v1alpha1
kind: WorkflowTemplate
metadata:
  name: signature-example-2
  annotations:
    scenarios.ai.sap.com/description: "Example for signature feature"
    scenarios.ai.sap.com/name: "signature-example-scenario"
    executables.ai.sap.com/description: "Output artifact example for multi signature feature"
    executables.ai.sap.com/name: "signature-example-multi-output-artifacts"
  labels:
    scenarios.ai.sap.com/id: "signature-example-scenario"
    executables.ai.sap.com/id: "signature-example-multi-out-art"
    ai.sap.com/version: "1.0.0"
spec:
  entrypoint: steps-example
  templates:
      # a template with two steps, each having an output artifact
    - name: steps-example
      steps:
        - - output-artifact-signatures-step1
        - - output-artifact-signatures-step2

    - name: output-artifact-signatures-step1
      outputs:
        # specify an output artifact named "dummy-model1"
        artifacts:
          - name: dummy-model1
            path: /tmp/model
            globalName: dummy-model1
        # the AICORE_ARTIFACT_SIGNATURES parameter can only hold artifact signatures of the current step, 
        # e.g. it could not hold the signature of "dummy-model2" below, because that is created in a different workflow step 
        parameters:
          - name: AICORE_ARTIFACT_SIGNATURES
            valueFrom:
                path: /tmp/signatures.json
      container:
        image: python:3.11-alpine
        imagePullPolicy: Always
        command: ["python", "-c"]
        args: 
            - >
              # ... skipped, as it will be the same as in the previous example

    - name: output-artifact-signatures-step2
      outputs:
        # specify an output artifact named "dummy-model2"
        artifacts:
          - name: dummy-model2
            path: /tmp/model
            globalName: dummy-model2
        # we need to define the AICORE_ARTIFACT_SIGNATURES parameter in each workflow step, where we want to provide 
        # signatures for an output artifact
        parameters:
          - name: AICORE_ARTIFACT_SIGNATURES
            valueFrom:
                path: /tmp/signatures.json
      container:
        image: python:3.11-alpine
        imagePullPolicy: Always
        command: ["python", "-c"]
        args: 
            - >
              # ... skipped, as it will be the same as in the previous example
```

This workflow template creates two output artifacts: ***dummy-model1*** and ***dummy-model2***, and their name-signature key-value-pairs in JSON format.



<a name="loio2f02a1d6e3974464a4dcf7bd85fcdcac__section_xzp_kgd_2yb"/>

## Verifying Signatures from Input Artifacts

If you use input artifacts with signatures in another execution, SAP AI Core provides the signatures of the artifacts as an environment variable named `AICORE_ARTIFACT_SIGNATURES`. The variable is a JSON key-value pair, where each key is the input artifact name and the value is its signature. For example:

```
{
  "name-of-model1": "signature-of-model1",
  "name-of-model2": "signature-of-model2"
}
```

To extract the signature, include the variable `AICORE_ARTIFACT_SIGNATURES` in your workflow template, that returns the value from the key of the pair, for example:

```
apiVersion: argoproj.io/v1alpha1
kind: WorkflowTemplate
metadata:
  name: signature-example-3
  annotations:
    scenarios.ai.sap.com/description: "Example for signature feature"
    scenarios.ai.sap.com/name: "signature-example-scenario"
    executables.ai.sap.com/description: "Input artifact example for signature feature"
    executables.ai.sap.com/name: "signature-example-input-artifacts"
  labels:
    scenarios.ai.sap.com/id: "signature-example-scenario"
    executables.ai.sap.com/id: "signature-example-in-art"
    ai.sap.com/version: "1.0.0"
spec:
  entrypoint: input-artifact-signatures-example
  templates:
    - name: input-artifact-signatures-example
      inputs:
        artifacts:
          - name: dummy-model
            path: /tmp/model
      container:
        image: python:3.11-alpine
        imagePullPolicy: Always
        command: ["python", "-c"]
        args: 
            - |
              import hashlib, json, os
              # create a hash of the input artifact to compare against the provided signature
              with open("/tmp/model", "rb") as f:
                  model_hash_actual = hashlib.file_digest(f, "sha256").hexdigest()
              # SAP AI Core will provide the artifact signature via the AICORE_ARTIFACT_SIGNATURES environment variable
              # it will be a string in JSON format
              signatures = json.loads(os.environ["AICORE_ARTIFACT_SIGNATURES"])
              model_hash_expected = signatures["dummy-model"]  # the name of the input artifact is the key
              assert model_hash_expected == model_hash_actual, "signatures did not match"
              print("success")
```

This template takes an input artifact with the name *<dummy-model\>*, calculates its signature, and compares it to the signature provided by SAP AI Core in the `AICORE_ARTIFACT_SIGNATURES` environment variable. The `AICORE_ARTIFACT_SIGNATURES` environment variable is only set when there is at least one input artifact with a signature, otherwise, it won’t be set at all. In a multi-step workflow template, the `AICORE_ARTIFACT_SIGNATURES` environment variable will be supplied to each step of the workflow template, irrespective of where the actual input artifact is defined. In each step, the `AICORE_ARTIFACT_SIGNATURES` variable will hold the signatures of the input artifacts from all steps.

