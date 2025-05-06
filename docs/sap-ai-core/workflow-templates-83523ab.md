<!-- loio83523ab8b49245bcbc9f1bf0969e32d8 -->

# Workflow Templates

Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.

Workflow templates help manage your training pipelines at the main tenant level. You can store these templates in your git repository and version them as needed. SAP AI Core executes workflows using the Argo Workflows open source project. Argo Workflows is an open-source, container-native workflow engine that orchestrates parallel jobs on Kubernetes. It's implemented as a Kubernetes CRD \(Custom Resource Definition\).

Workflow templates act as `executables`. To map them, you need certain attributes in your template's `metadata` section. The AI API uses the `annotations` and `labels` in the template to find scenarios and executables.

Workflow templates are built on the Argo Workflows engine and are defined as `WorkflowTemplates`. These are your cluster's workflow definitions. For more information about `WorkflowTemplates` and sample workflows, see the Argo documentation.

In SAP AI Core, Argo Workflows are used to:

-   Train models

-   Ingest data

-   Preprocess and postprocess data

-   Execute batch inference pipelines


Workflows are executed in batch mode. A workflow can produce multiple output artifacts, but only an output artifact with a `globalName` is considered to be the final output artifact of the workflow.

> ### Restriction:
> Output artifacts can only use the default object store

For the model training code, SAP AI Core is language-agnostic. However, you need to specify the relevant programming language in the workflow parameters. If you're importing any packages, list them in a separate file named `requirements.txt` and store it in the same directory.

> ### Restriction:  
> The maximum number of workflow templates is limited at tenant level to 50. If you reach this limit, you will receive an error message. To free up space, delete some workflow templates. Alternatively, raise a ticket to increase your quota.

To get started, copy the generic workflow template below and add your own values as required. You can use any text editor with a YAML plugin to create your templates. Workflows support the following parameters:



**Workflow Template Parameters**


<table>
<tr>
<th valign="top">

Type

</th>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

name \(mandatory\)

</td>
<td valign="top">

–

</td>
<td valign="top">

The executable ID. The executable ID must be unique among all executables available within the SAP AI Core main tenant.

</td>
</tr>
<tr>
<td valign="top">

labels \(mandatory\)

</td>
<td valign="top">

`ai.sap.com/resourcePlan`

</td>
<td valign="top">

You must specify the chosen `resourcePlan`. The value is the string value of the selected resource plan. For more information, see [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md).

</td>
</tr>
<tr>
<td valign="top" rowspan="8">

annotations

</td>
<td valign="top">

`scenarios.ai.sap.com/description` \(optional\)

</td>
<td valign="top">

A description of the scenario to which this executable belongs.

</td>
</tr>
<tr>
<td valign="top">

`scenarios.ai.sap.com/name` \(mandatory\)

</td>
<td valign="top">

The scenario name, which is necessary for the AI API to discover a scenario.

</td>
</tr>
<tr>
<td valign="top">

`executables.ai.sap.com/description` \(optional\)

</td>
<td valign="top">

The description of an executable.

</td>
</tr>
<tr>
<td valign="top">

`executables.ai.sap.com/name` \(mandatory\)

</td>
<td valign="top">

The name of the executable.

</td>
</tr>
<tr>
<td valign="top">

`artifacts.ai.sap.com/<argo_artifact_name>.suffix`

</td>
<td valign="top">

A suffix added to the file or folder of the output artifact on the object store.

</td>
</tr>
<tr>
<td valign="top">

`artifacts.ai.sap.com/<argo_artifact_name>.kind`

</td>
<td valign="top">

The type of output artifact \(for example, a dataset or model\).

</td>
</tr>
<tr>
<td valign="top">

`artifacts.ai.sap.com/<argo_artifact_name>.name`

</td>
<td valign="top">

The name under which the output artifact is registered in the AI API.

</td>
</tr>
<tr>
<td valign="top">

`artifacts.ai.sap.com/<argo_artifact_name>.description` \(optional\)

`artifacts.ai.sap.com/<argo_artifact_name>.labels: | {"ext.ai.sap.com/customkey1":"customvalue1", "ext.ai.sap.com/customkey2":"customvalue2"}` \(optional\)

</td>
<td valign="top">

You can add further metadata for an artifact using these annotations.

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`labels`

</td>
<td valign="top">

`scenarios.ai.sap.com/id` \(mandatory\)

</td>
<td valign="top">

The scenario ID to which the workflow template belongs.

</td>
</tr>
<tr>
<td valign="top">

`ai.sap.com/version` \(mandatory\)

</td>
<td valign="top">

The compatibility version of this executable. You can use the compatibility versions to offer executables in different variants for different AI service consumers.

</td>
</tr>
</table>

> ### Note:  
> In the artifact-related parameters above, `<argo_artifact_name>` refers to the `globalName` of an output artifact.



<a name="loio83523ab8b49245bcbc9f1bf0969e32d8__section_dgg_cpd_q5b"/>

## Generic Workflow Template

```
apiVersion: argoproj.io/v1alpha1
kind: WorkflowTemplate
metadata:
  name: text-clf-train-tutorial
  annotations:
    scenarios.ai.sap.com/description: "SAP developers tutorial scenario"
    scenarios.ai.sap.com/name: "text-clf-tutorial-scenario"
    executables.ai.sap.com/description: "Text classification Scikit training executable"
    executables.ai.sap.com/name: "text-clf-train-tutorial-exec"
    artifacts.ai.sap.com/text-data.kind: "dataset"
    artifacts.ai.sap.com/text-model-tutorial.kind: "model"
    artifacts.ai.sap.com/text-model-tutorial.description: "artifact description"
    artifacts.ai.sap.com/text-model-tutorial.labels: | 
        {"ext.ai.sap.com/customkey1":"customvalue1", "ext.ai.sap.com/customkey2":"customvalue2"}
  labels:
    scenarios.ai.sap.com/id: "text-clf-tutorial"
    executables.ai.sap.com/id: "text-clf-train-tutorial"
    ai.sap.com/version: "1.0.0"
spec:
  imagePullSecrets:
    - name: <name of your Docker registry secret>
  entrypoint: text-clf-sk-training
  arguments:
    parameters: # placeholder for string like inputs
      - name: DEPTH # identifier local to this workflow
        description: description of the parameter
        default: test
  templates:
    - name: text-clf-sk-training
      metadata:
        labels:
          ai.sap.com/resourcePlan: starter
      inputs:
        artifacts:
          - name: text-data
            path: /app/data/
      outputs:
        artifacts:
          - name: text-model-tutorial
            path: /app/model
            globalName: text-model-tutorial
            archive:
              none: {}
      container:
        image: "<DOCKER IMAGE URL GOES HERE>"
        imagePullPolicy: Always
        command: ["/bin/sh", "-c"]
        args:
          - >
            set -e && echo "---Start Training---" && python /app/src/train_scikit.py && ls -lR /app/model && echo "---End Training---"
```

> ### Note:  
> For every container in the template, the `command: ["/bin/sh", "-c"]` field is mandatory. The contents of the argument can be amended, but must not be empty. The `CMD` and `ENDPOINT` specified in the Dockerfile of a container are ignored.

User ID and group ID 65534 is required to run the Docker image. This user has permission to access the files while the application is running. You can check and change the permissions by using the `chown` and `chmod` commands.

> ### Tip:  
> To make sure that the container is working as expected before submitting it to SAP AI Core, run <code>docker run -it --user 65534:65543 <i class="varname">&lt;docker-image&gt;</i></code> locally.

> ### Note:  
> The `archive: none: {}` option in the `outputs artifacts` sections disables automatic archiving for the artifact. If archiving is enabled, the output artifacts are archived to a `tar-gzip` file before they are uploaded to the object store. If archiving is disabled through `archive: none: {}`, the artifact will be uploaded to the object store in its current format. If the output artifact points to a directory, the directory will be uploaded “as is” to the object store. However, object stores in SAP HANA Cloud, data lake do not support this. In this case, remove `archive: none: {}` and archive the directory to a single `tar-gzip` file before it is uploaded to the object store.

> ### Note:  
> When multiple containers are defined in a single WorkflowTemplate, for example when using Sidecar or Container Set, one of the containers must be named \`main\`. To fetch logs of another container in the same template using the a GET request to the endpoint `/logs`, the name of the container must have the \`readable-\` prefix. The execution can still run without the \`readable-\` prefix, but logs will be inaccessible through the endpoint.. For more information, see [Argo Sidecar](https://argoproj.github.io/argo-workflows/walk-through/sidecars) and [Argo Container Set](https://argoproj.github.io/argo-workflows/container-set-template/).



<a name="loio83523ab8b49245bcbc9f1bf0969e32d8__section_m4l_4cy_3wX"/>

## Sync an Application Manually

Applications sync with your GitHub repository automatically at intervals of ~3 minutes. Use the endpoint below to manually request a sync:`{{apiurl}}/admin/applications/{{appName}}/refresh`

**Parent topic:**[Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[List Scenarios](list-scenarios-deedde5.md "A scenario is an implementation of a specific AI use case within a user's tenant. It consists of a pre-defined set of AI capabilities in the form of executables and templates.")

[List Executables](list-executables-80895a4.md "An executable is a reusable template that defines a workflow or pipeline for tasks such as training a machine learning model or creating a deployment. It contains placeholders for input artifacts (datasets or models) and parameters (custom key-pair values) that enable the template to be reused in different scenarios.")

[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references (such as datasets or models), and environment settings that are used to instantiate and run an execution or deployment of an executable or template.")

[List Configurations](list-configurations-8074b2a.md "")

[Using Artifact Signatures](using-artifact-signatures-2f02a1d.md "Artifact signatures in the form of a hash can be added to output artifacts from executions.")

[Start Training](start-training-54b44e4.md "")

[Stop Training Instances](stop-training-instances-3d85344.md "")

[Delete Training Instances](delete-training-instances-612ce17.md "")

[Efficiency Features](efficiency-features-4cb76f7.md "Discover features of the SAP AI Core runtime that improve efficiency and help manage resource consumption.")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "Deployment and execution logs contain information about API processing and metrics.")

[Training Schedules](training-schedules-2b702f8.md "")

<a name="concept_vwr_y1k_lwb"/>

<!-- concept\_vwr\_y1k\_lwb -->

## Stop or Delete Multiple Training Instances



The feature is set to false by default. To enable bulk PATCH operations, your template must contain the following snippet, with the relevant values set to `true`.

```

Meta:
  "bulkUpdates": {
        "executions": false,
        "deployments": false
      }
```

**Related Information**  


[Argo Workflows](https://argoproj.github.io/argo-workflows/)

[Register Your Docker Registry Secret](register-your-docker-registry-secret-a7cf5e1.md "Docker packages and runs applications in remote containers. Connect SAP AI Core to a Docker repository and manage access using a Docker registry secret.")

[Stop Multiple Training Instances](stop-multiple-training-instances-09b4810.md "")

[Delete Multiple Training Instances](delete-multiple-training-instances-c1c3cc3.md "")

