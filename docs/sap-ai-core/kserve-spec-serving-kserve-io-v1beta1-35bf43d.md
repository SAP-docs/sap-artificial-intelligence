<!-- loio35bf43d700784453bd11a8c2a9125b2e -->

# KServe Spec serving.kserve.io/v1beta1

Package `v1beta1` contains API Schema definitions for the serving `v1beta1` API group \(`serving.kserve.io/v1beta1`\).



<a name="loio35bf43d700784453bd11a8c2a9125b2e__section_inferenceservice"/>

## InferenceService

InferenceService is the schema for the InferenceServices API.


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`metadata`

[Kubernetes meta/v1.ObjectMeta](https://v1-18.docs.kubernetes.io/docs/reference/generated/kubernetes-api/v1.18/#objectmeta-v1-meta)

</td>
<td valign="top">

Refer to the Kubernetes API documentation for the fields of the `metadata` field.

</td>
</tr>
<tr>
<td valign="top">

`spec`

[KServe InferenceServiceSpec](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_inferenceservicespec)

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`predictor`

[KServe PredictorSpec](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_predictorspec)

</td>
<td valign="top">

Predictor defines the model serving spec

</td>
</tr>
</table>



</td>
</tr>
</table>



<a name="loio35bf43d700784453bd11a8c2a9125b2e__section_kfserving_metadata_annotations"/>

## KServe Metadata Annotations

\(Appears on [InferenceService](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_inferenceservice)\)

A multiline string containing a subset of supported KServe Metadata Labels. You can add a placeholder using `{{variable_name}}` to define a variable and replace the value dynamically. For example:

```
autoscaling.knative.dev/target: "{{inputs.parameters.MyAutoScalingTarget}}"
```


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Description

</th>
<th valign="top">

Default Value

</th>
</tr>
<tr>
<td valign="top">

`autoscaling.knative.dev/metric` 

</td>
<td valign="top">

Metric to be used for autoscaling.

Allowed values:

-   `concurrency`
-   `rps`



</td>
<td valign="top">

`concurrency`

</td>
</tr>
<tr>
<td valign="top">

`autoscaling.knative.dev/target` 

</td>
<td valign="top">

Target value for the configured metric.

Allowed values: integer

</td>
<td valign="top">

100

</td>
</tr>
<tr>
<td valign="top">

`autoscaling.knative.dev/targetBurstCapacity` 

</td>
<td valign="top">

Size of traffic burst deployment can handle without buffering.

Allowed values: Float \(0 means requests will only be buffered when number of replicas is 0; -1 means the request is always buffered\)

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

`autoscaling.knative.dev/window` 

</td>
<td valign="top">

Amount of time that autoscaler uses before making decisions. The smaller the number, the faster the autoscaler will react.

Allowed values: Integer in seconds \(s\) or hours \(h\)

</td>
<td valign="top">

60s

</td>
</tr>
<tr>
<td valign="top">

`autoscaling.knative.dev/scaleToZeroPodRetentionPeriod`

</td>
<td valign="top">

Minimum amount of time that the last pod will remain active after the Autoscaler decides to scale pods to zero.

Allowed values: Non-negative duration string

</td>
<td valign="top">

0s

</td>
</tr>
</table>

> ### Example:  
> ```
> metadata:
>    annotations: |
>       autoscaling.knative.dev/metric: rps
>       autoscaling.knative.dev/target: {{inputs.parameters.MyAutoScalingTarget}}
>       autoscaling.knative.dev/targetBurstCapacity: 0
>       autoscaling.knative.dev/window: 10s
> ```



<a name="loio35bf43d700784453bd11a8c2a9125b2e__section_kfserving_metadata_labels"/>

## KServe Metadata Labels

\(Appears on [InferenceService](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_inferenceservice)\)

A multiline string containing a subset of supported KServe Metadata Labels. You can add a placeholder using `{{variable_name}}` to define a variable and replace the resource plan dynamically. For example:

```
ai.sap.com/resourcePlan:
                    "{{inputs.parameters.MyResourcePlan}}"
```


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`ai.sap.com/resourcePlan` 

</td>
<td valign="top">

Resource Plan to be used in creating the KServe-based Model Server \(for example, “basic”\)

</td>
</tr>
</table>

> ### Example:  
> ```
> metadata:
>    labels: |
>       ai.sap.com/resourcePlan: basic
> ```



<a name="loio35bf43d700784453bd11a8c2a9125b2e__section_inferenceservicespec"/>

## KServe InferenceServiceSpec

\(Appears on [InferenceService](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_inferenceservice)\)

InferenceServiceSpec is the top level type for this resource.


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`predictor`

[KServe PredictorSpec](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_predictorspec)

</td>
<td valign="top">

Predictor defines the model serving spec

</td>
</tr>
</table>



<a name="loio35bf43d700784453bd11a8c2a9125b2e__section_predictorspec"/>

## KServe PredictorSpec

\(Appears on [KServe InferenceServiceSpec](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_inferenceservicespec)\)

PredictorSpec defines the configuration for a predictor. The following fields follow a “1-of” semantic. Users must specify exactly one spec.


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`containers`

[Kubernetes core/v1.Container](https://v1-18.docs.kubernetes.io/docs/reference/generated/kubernetes-api/v1.18/#container-v1-core)

</td>
<td valign="top">

List of containers belonging to the pod. Containers cannot currently be added or removed. There must be at least one container in a pod, cannot be updated.

</td>
</tr>
<tr>
<td valign="top">

`imagePullSecrets` 

[Kubernetes core/v1.LocalObjectReference](https://v1-18.docs.kubernetes.io/docs/reference/generated/kubernetes-api/v1.18/#localobjectreference-v1-core) 

</td>
<td valign="top">

List of references to secrets in the same resource group, and used for pulling any of the images used by this spec. The name of the secret must be the same as the one created via Docker Registry Secret creation API. For more information, see [Specifying imagePullSecrets on a Pod](https://kubernetes.io/docs/concepts/containers/images#specifying-imagepullsecrets-on-a-pod).

</td>
</tr>
<tr>
<td valign="top">

`minReplicas` \(optional\)

int

</td>
<td valign="top">

Minimum number of replicas. Defaults to 1 but can be set to 0 to enable scale-to-zero.

AI Core will attempt, on best-case effort, to schedule your deployments in different availability zone when you have more than one replica. This way, you can make your deployment High-Available \(HA\) by configuring min and max-replica accordingly.

</td>
</tr>
<tr>
<td valign="top">

`maxReplicas` \(optional\)

int

</td>
<td valign="top">

Maximum number of replicas for autoscaling. Default: if minReplicas \>= 2 then maxReplicas = minReplicas else 2.

AI Core will attempt, on best-case effort, to schedule your deployments in different availability zone when you have more than one replica. This way, you can make your deployment High-Available \(HA\) by configuring min and max-replica accordingly.

</td>
</tr>
<tr>
<td valign="top">

`containerConcurrency` \(optional\)

int64

</td>
<td valign="top">

Specifies how many requests can be processed concurrently, this sets the hard limit of the container concurrency.

\([https://knative.dev/docs/serving/autoscaling/concurrency](https://knative.dev/docs/serving/autoscaling/concurrency)\).

</td>
</tr>
<tr>
<td valign="top">

`timeout` \(optional\)

int64

</td>
<td valign="top">

Specifies the number of seconds to wait before timing out a request to the component.

</td>
</tr>
<tr>
<td valign="top">

`terminationGracePeriodSeconds` \(optional\)

int64

</td>
<td valign="top">

Optional duration in seconds that the pod needs to terminate gracefully, may be decreased in delete request. Value must be non-negative integer. The value zero indicates delete immediately. If this value is nil, the default grace period will be used instead. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. Defaults to 30 seconds.

</td>
</tr>
</table>

> ### Example:  
> ```
> spec: |
>    predictor:
>       imagePullSecrets:
>        - name: [DOCKER REGISTRY SECRET GOES HERE]
>       minReplicas: 1
>       maxReplicas: 5
>       containers:
>       - name: kserve-container
>          image: "[DOCKER IMAGE URL GOES HERE]"
>          ports:
>          - containerPort: 9001
>             protocol: TCP
>          env:
>          - name: STORAGE_URI
>             value: "{{inputs.artifacts.textmodel}}"
> ```

**Parent topic:**[Serving Template API Reference](serving-template-api-reference-51b2271.md "")

**Related Information**  


[API Schema Spec ai.sap.com/v1alpha1](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md "Package valpha1 contains API Schema definitions for the serving v1alpha1 API group (ai.sap.com/v1alpha1).")

