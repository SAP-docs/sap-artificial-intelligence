<!-- loio83523ab8b49245bcbc9f1bf0969e32d8 -->

# Workflow Templates

Here, you can find a minimal workflow example template, that can be adapted to meet the requirements of your workflow.

Workflow templates allow you to manage your training pipelines at the level of the main tenant. Templates are stored in your git repository, where you can version them as required. Workflows in SAP AI Core are executed using the Argo Workflows open source project. Argo Workflows is an open-source, container-native workflow engine for orchestrating parallel jobs on Kubernetes. Argo Workflows is implemented as a Kubernetes CRD \(Custom Resource Definition\).

Workflow templates are mapped as `executables`. Mapping requires certain attributes in the `metadata` section of your template. The AI API uses the `annotations` and `labels` in the template to locate scenarios and executables.

Workflow templates are based on the Argo Workflows workflow engine and are defined as `WorkflowTemplates`. These are definitions of workflows in your cluster. For information about `WorkflowTemplates` and sample workflows, see the Argo documentation.

In SAP AI Core, Argo Workflows is used to:

-   Train models

-   Ingest data

-   Preprocess and postprocess data

-   Execute batch inference pipelines


The workflows are executed in batch mode.

For the model training code, SAP AI Core is language agnostic, however the relevant programming language must be specified in the workflow parameters, and any imported packages must be specified in `requirements.txt`.

In SAP AI Core, workflow templates are mapped as `executables`. Mapping requires certain attributes in the `metadata` section of your template.

To get started, copy the generic workflow template below and add your own values as required. You can use any text editor with a YAML plugin to create the templates. Workflows support the following parameters:



**Workflow Template Output Artifact Parameters**


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

\-



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

You must specify the chosen `resourcePlan`. The value is the string value of the selected resource plan selected \(see [Choose a Resource Plan](choose-a-resource-plan-57f4f19.md)\).



</td>
</tr>
<tr>
<td valign="top" rowspan="7">

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

Scenario name, which is necessary for the AI API to discover a scenario.



</td>
</tr>
<tr>
<td valign="top">

`executables.ai.sap.com/description`

\(optional\)



</td>
<td valign="top">

Description of an executable.



</td>
</tr>
<tr>
<td valign="top">

`executables.ai.sap.com/name` \(mandatory\)



</td>
<td valign="top">

Name of the executable.



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
  labels:
    scenarios.ai.sap.com/id: "text-clf-tutorial"
    executables.ai.sap.com/id: "text-clf-train-tutorial"
    ai.sap.com/version: "1.0.0"
spec:
  imagePullSecrets:
    - name: <name of your Docker registry secret>
  entrypoint: text-clf-sk-training
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
> For every container in the template, the `command: ["/bin/sh", "-c"]` field is mandatory. The contents of the argument can be ammended, but must not be empty. The `CMD` and `ENDPOINT` specified in the Dockerfile of a container are ignored.



<a name="loio83523ab8b49245bcbc9f1bf0969e32d8__section_m4l_4cy_3wX"/>

## Sync an Application Manually



### Applications sync with your GitHub repository automatically at intervals of ~3 minutes. Use the endpoint below to manually request a sync:

`{{apiurl}}/admin/applications/{{appName}}/refresh`

**Parent topic:** [Train Your Model](train-your-model-a9ceb06.md "You execute a training workflow to train your AI learning model.")

**Related Information**  


[Choose a Resource Plan](choose-a-resource-plan-57f4f19.md "You can configure SAP AI Core to use different infrastructure resources for different tasks, based on task demand. SAP AI Core provides several preconfigured infrastructure bundles called “resource plans” for this purpose.")

[List Scenarios](list-scenarios-deedde5.md "A scenario is a group of related executables for a use case within the user's tenant. A scenario can have multiple versions that further correspond to the different versions of executables.")

[List Executables](list-executables-80895a4.md "An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment. You can list all of the executables in a scenario and get details of specific executables from a scenario. Workflow templates are mapped to training executables.")

[Create Configurations](create-configurations-884ae34.md "A configuration is a collection of parameters, artifact references, and executables that are used to run an execution or deployment.")

[List Configurations](list-configurations-8074b2a.md "")

[Start Training](start-training-54b44e4.md "Start training and check the status of the execution.")

[Stop Training Instances](stop-training-instances-3d85344.md#loio3d853443027449d9a33723165b19b25a "")

[Delete Training Instances](delete-training-instances-612ce17.md#loio612ce172e609432a840a22eb211ecf7b "Deleting a training instance releases the SAP AI Core resources that it used.")

[Retrieve Execution Logs](retrieve-execution-logs-fbc55d3.md "Information about API processing and metrics, are stored and accessed in the deployment and execution logs.")

[Training Schedules](training-schedules-2b702f8.md "")

[Argo Workflows](https://argoproj.github.io/argo-workflows/)

[Register Your Docker Registry Secret](register-your-docker-registry-secret-a7cf5e1.md "Your Docker credentials are managed using secrets. Secrets are allow and control connections across directories and tools, without compromising your credentials.")

[Stop Multiple Training Instances](stop-training-instances-3d85344.md#loio09b4810ad29445d19025836ed1ac5151 "")

[Delete Multiple Training Instances](delete-training-instances-612ce17.md#loioc1c3cc3e3f88417ba785ab8e29564e82 "")

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


[Stop Multiple Training Instances](stop-training-instances-3d85344.md#loio09b4810ad29445d19025836ed1ac5151 "")

[Delete Multiple Training Instances](delete-training-instances-612ce17.md#loioc1c3cc3e3f88417ba785ab8e29564e82 "")

