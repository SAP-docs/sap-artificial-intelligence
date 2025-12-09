<!-- loio20a8667ef19e4de59a4469cb542a7457 -->

# Serving Templates

You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.

Serving templates are used to deploy one or more trained models on a model server, which process incoming inference requests and returns the results from the machine learning model. Serving templates are stored in your git repository, where you can version them as required.

In SAP AI Core, serving templates are mapped as `executables`. Mapping requires certain attributes in the `metadata` section of your template.

Models are deployed using a simple Kubernetes Custom Resource Definition \(CRD\), which is provided by KServe. To deploy a model, you must provide a YAML specification that follows the KServe specification and that defines the required input parameters and artifacts.

> ### Restriction:  
> The maximum number of serving templates is limited at tenant level to 50. If you reach this limit, you receive an error message. To free up space, delete some serving templates. Alternatively, raise a ticket to increase your quota.

To get started, copy the generic serving template below and add your own values as required. You can use any text editor with a YAML plugin to create the templates. Your YAML specification must follow the KServe specs and define the required input parameters and artifacts.



**Serving Template Parameter Details**


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

`name` \(mandatory\)

</td>
<td valign="top">

 

</td>
<td valign="top">

The executable ID. The executable ID must be unique among all executables available within the SAP AI Core main tenant.

</td>
</tr>
<tr>
<td valign="top">

metadata \(mandatory\)

</td>
<td valign="top">

`name`

</td>
<td valign="top">

The technical ID of the serving template that is used to uniquely identify the serving template. It is specified as the serving Template's executable ID, and therefore must be unique among all executables available within the SAP AI Core main tenant.

</td>
</tr>
<tr>
<td valign="top" rowspan="6">

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

`executables.ai.sap.com/description` \(optional\)

</td>
<td valign="top">

A description of the serving template.

</td>
</tr>
<tr>
<td valign="top">

`executables.ai.sap.com/name` \(mandatory\)

</td>
<td valign="top">

The name of the serving template.

</td>
</tr>
<tr>
<td valign="top">

`executables.ai.sap.com/cascade-update-deployments` \(optional\)

</td>
<td valign="top">

Setting to allow changes to the serving template to be cascaded to associated deployments. See [Change Serving Template and Update Deployments](change-serving-template-and-update-deployments-9555fe1.md).

</td>
</tr>
<tr>
<td valign="top">

<code>artifacts.ai.sap.com/<i class="varname">&lt;argo_artifact_name&gt;</i>.description</code> \(optional\)

<code>artifacts.ai.sap.com/<i class="varname">&lt;argo_artifact_name&gt;</i>.labels: | {"ext.ai.sap.com/customkey1":"customvalue1", "ext.ai.sap.com/customkey2":"customvalue2"}</code> \(optional\)

</td>
<td valign="top">

You can add further metadata for an artifact using these annotations.

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

labels

</td>
<td valign="top">

`scenarios.ai.sap.com/id` \(mandatory\)

</td>
<td valign="top">

The scenario ID to which the serving template belongs

</td>
</tr>
<tr>
<td valign="top">

`ai.sap.com/version` \(mandatory\)

</td>
<td valign="top">

The version is intended for customer usage to identify compatible serving template versions.

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

spec

</td>
<td valign="top">

`imagePullSecret`\(Optional\)

Not required if your Docker image is fetched from a public docker repository.

</td>
<td valign="top">

[Register Your Docker Registry Secret](register-your-docker-registry-secret-a7cf5e1.md).

</td>
</tr>
<tr>
<td valign="top">

`minReplicas` \(Optional\)

</td>
<td valign="top">

Deployments run continually by default, but can be stopped manually when inferences are not needed. Setting minReplicas to `0` allows the inference server to enter the stopped state, when not in use. When needed, it is restarted and nodes scaled, based on demand and the min/maxReplicas parameter. For more information see [Efficiency Features](efficiency-features-9fad26a.md).

</td>
</tr>
<tr>
<td valign="top">

`maxReplicas` \(Optional\)

</td>
<td valign="top">

Limit the number of nodes that the inference server scales up to. For more information see [Efficiency Features](efficiency-features-9fad26a.md).

</td>
</tr>
<tr>
<td valign="top">

labels \(mandatory\)

</td>
<td valign="top">

Choose one of the following:

-   `ai.sap.com/resourcePlan`
-   `ai.sap.com/instanceType`



</td>
<td valign="top">

You must specify a `resourcePlan` or `instanceType`. The value is the string value of the selected item. For more information, see [Choose an Instance](choose-an-instance-57f4f19.md). For available`instanceType`s, see SAP Note [3660109](https://me.sap.com/notes/3660109) . For available `resourcePlan`s, see[Table 1](choose-an-instance-57f4f19.md#loio57f4f19d9b3b46208ee1d72017d0eab6__table_qzy_f4n_zqb) .

> ### Tip:  
> `instanceType`s are recommended because they provide access to newer hardware and higher performance specifications compared to `resourcePlan`s.



</td>
</tr>
</table>



<a name="loio20a8667ef19e4de59a4469cb542a7457__section_bb3_c4x_p5b"/>

## Generic Serving Template

```
apiVersion: ai.sap.com/v1alpha1
kind: ServingTemplate
metadata:
  name: text-clf-infer-tutorial
  annotations:
    scenarios.ai.sap.com/description: "SAP developers tutorial scenario"
    scenarios.ai.sap.com/name: "text-clf-tutorial-scenario"
    executables.ai.sap.com/description: "Inference executable for text classification with Scikit-learn"
    executables.ai.sap.com/name: "text-clf-infer-tutorial-exec"
    artifacts.ai.sap.com/textmodel.kind: "model"
    artifacts.ai.sap.com/textmodel.description: "artifact description"
    artifacts.ai.sap.com/textmodel.labels: | 
        {"ext.ai.sap.com/customkey1":"customvalue1", "ext.ai.sap.com/customkey2":"customvalue2"}
  labels:
    ai.sap.com/version: 0.1.0
    scenarios.ai.sap.com/id: "text-clf-tutorial" 
spec:
  inputs:
    parameters:
      - name: modelName
        default: value
        type: string
        description: description of the parameter
      - name: image
        default: default-image-value
        type: string
        description: description of the parameter
    artifacts:
      - name: textmodel
  template:
    apiVersion: "serving.kserve.io/v1beta1"
    metadata:
      annotations: |
        autoscaling.knative.dev/metric: rps
        autoscaling.knative.dev/target: 100
        autoscaling.knative.dev/targetBurstCapacity: 70
      labels: |
        ai.sap.com/instanceType: <yourChoiceOfInstanceType> # or ai.sap.com/resourcePlan: <yourChoiceOfresourcePlan>
    spec: |
      predictor:
        imagePullSecrets:
          - name: <Name of your Docker registry secret>
        minReplicas: 0
        maxReplicas: 5
        containers:
        - name: kserve-container
          image: {{inputs.parameters.image}}
          ports:
          - containerPort: 9001
            protocol: TCP
          env:
          - name: STORAGE_URI
            value: "{{inputs.artifacts.textmodel}}"
```



-   STORAGE\_URI environment variable name is currently hard-coded in KServe to indicate that the model should be downloaded when a custom predictor is configured with the env varSTORAGE\_URI.
-   /mnt/models is currently hard-coded in KServe. When you try this example with your own docker container, read the models from that path.

> ### Caution:  
> In the example above, the image parameter is provided as an input. The image value is resolved during rendering, based on priority. `{{inputs.parameters.image}}` can be rendered from two possible sources, with the following priority:
> 
> 1.  The image value may be specified in `configuration/<configuration_id>` when creating the configuration
> 
>     ```
>     curl --location --request POST '{{apiurl}}/v2/lm/configurations'  \
>     --header 'AI-Resource-Group: default' \
>     --header 'Authorization: Bearer {TOKEN}' \
>     --header 'Content-Type: application/json' \
>     --data-raw '{
>       "name": "<configuration_id>",
>       "executableId": "<executable_id>",
>       "scenarioId": "<scenario_id>",
>       "versionId": "0.1.0",
>       "parameterBindings": [
>         {
>           "key": "image",
>           "value": "source-1-image-value"
>         }
>       ],
>       "inputArtifactBindings": [
>       ]
>     }'
>     ```
> 
> 2.  The default image value may be specified in the ServingTemplate
> 
>     ```
>     spec:
>       inputs:
>         parameters:
>         - default: "default-image-value"
>           name: image
>           type: string
>     ```
> 
> 
> If source 1 exists, updating the default value in source 2 will NOT affect the rendered deployment image.
> 
> If source 1 does not exist, the deployment image will use \(and respond to changes in\) the default value from source 2.



<a name="loio20a8667ef19e4de59a4469cb542a7457__section_m4l_4cy_3wX"/>

## Sync an Application Manually

Applications sync with your GitHub repository automatically at intervals of ~3 minutes. Use the endpoint below to manually request a sync:`{{apiurl}}/admin/applications/{{appName}}/refresh`

-   **[Template Synchronization](template-synchronization-298d392.md "Your GitOps implementation integrates with SAP AI
									Core to enable CI/CD. Templates sync from your
		Git repository to a Kubernetes cluster. Your training and serving templates are regularly
		synchronized every few minutes. SAP AI
									Core checks the template syntax, and if
		synchronization fails, it displays error messages.")**  
Your GitOps implementation integrates with SAP AI Core to enable CI/CD. Templates sync from your Git repository to a Kubernetes cluster. Your training and serving templates are regularly synchronized every few minutes. SAP AI Core checks the template syntax, and if synchronization fails, it displays error messages.
-   **[Change Serving Template and Update Deployments](change-serving-template-and-update-deployments-9555fe1.md "If you change a serving template, you can automatically update the deployments that are associated with that template.")**  
If you change a serving template, you can automatically update the deployments that are associated with that template.

<a name="concept_dcw_41k_lwb"/>

<!-- concept\_dcw\_41k\_lwb -->

## Stop or Delete Multiple Deployments



The feature is set to false by default. To enable bulk PATCH operations, your template must contain the following snippet, with the relevant values set to `true`.

```

Meta:
  "bulkUpdates": {
        "executions": false,
        "deployments": false
      }
```

**Related Information**  


[Stop Multiple Deployments](stop-multiple-deployments-331cdf5.md "")

[Delete Multiple Deployments](delete-multiple-deployments-6b521aa.md "")

