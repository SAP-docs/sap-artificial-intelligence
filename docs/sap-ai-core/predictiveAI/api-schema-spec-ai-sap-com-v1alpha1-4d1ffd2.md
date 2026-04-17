<!-- loio4d1ffd2507e94d9f8690298d88e41671 -->

# API Schema Spec ai.sap.com/v1alpha1

Package `valpha1` contains API Schema definitions for the serving `v1alpha1` API group \(`ai.sap.com/v1alpha1`\).



<a name="loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate"/>

## ServingTemplate

ServingTemplate is a type of executable that specifies how a model is to be served.


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

[Kubernetes meta/v1.ObjectMeta](https://v1-20.docs.kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#objectmeta-v1-meta)

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`name` 

</td>
<td valign="top">

\(Mandatory\) Technical ID of the serving template that is used to uniquely identify the serving template.

</td>
</tr>
<tr>
<td valign="top">

`annotations`

[ServingTemplate Metadata Annotations](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_metadata_annotations)

</td>
<td valign="top">

Annotations to define the Scenario and Executable info.

</td>
</tr>
<tr>
<td valign="top">

`labels`

[ServingTemplate Metadata Labels](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_metadata_labels)

</td>
<td valign="top">

Labels to define the Scenario and Executable info.

</td>
</tr>
</table>



</td>
</tr>
<tr>
<td valign="top">

`spec`

[ServingTemplate Spec](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_spec)

</td>
<td valign="top">

ServingTemplateSpec contains a template for KServe, input parameters and artifacts required to create a KServe CR.

</td>
</tr>
</table>



<a name="loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_metadata_annotations"/>

## ServingTemplate Metadata Annotations

\(Appears on [ServingTemplate](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate)\)

A subset of supported Kubernetes Metadata Annotations


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

`scenarios.ai.sap.com/description` 

</td>
<td valign="top">

A description of the Scenario \(for example, “SAP developers tutorial scenario”\)

</td>
</tr>
<tr>
<td valign="top">

`scenarios.ai.sap.com/name` 

</td>
<td valign="top">

The name of the serving template \(for example, “text-clf-tutorial-scenario”\)

</td>
</tr>
<tr>
<td valign="top">

`executables.ai.sap.com/description` 

</td>
<td valign="top">

A description of the serving template. \(for example, “Inference executable for text classification with Scikit-learn”\)

</td>
</tr>
<tr>
<td valign="top">

`executables.ai.sap.com/name` 

</td>
<td valign="top">

The name of the serving template \(for example, “text-clf-infer-tutorial-exec”\)

</td>
</tr>
</table>



<a name="loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_metadata_labels"/>

## ServingTemplate Metadata Labels

\(Appears on [ServingTemplate](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate)\)

A subset of supported Kubernetes Metadata Labels


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

`ai.sap.com/version` 

</td>
<td valign="top">

Version of the Scenario \(for example, “1.0.0”\)

</td>
</tr>
<tr>
<td valign="top">

`scenarios.ai.sap.com/id` 

</td>
<td valign="top">

Unique ID of the Scenario \(for example, “1234-abcd-efg”\)

</td>
</tr>
</table>



<a name="loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_spec"/>

## ServingTemplate Spec

\(Appears on [ServingTemplate](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate)\)

ServingTemplate spec is the top level type for this resource.


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

`inputs`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`parameters`

[ServingTemplate Input Parameters](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_input_parameters)

</td>
<td valign="top">

Input parameters for the [KServe InferenceService Template](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_kserve_template)

</td>
</tr>
<tr>
<td valign="top">

`artifacts`

[ServingTemplate Input Artifacts](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_input_artifacts)

</td>
<td valign="top">

Input artifacts for the [KServe InferenceService Template](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_kserve_template)

</td>
</tr>
</table>



</td>
</tr>
<tr>
<td valign="top">

`template`

[KServe InferenceService Template](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_kserve_template)

</td>
<td valign="top">

KServe CR template

</td>
</tr>
</table>



<a name="loio4d1ffd2507e94d9f8690298d88e41671__section_input_parameters"/>

## ServingTemplate Input Parameters

\(Appears on [ServingTemplate Spec](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_spec)\)

Input parameters required for [KServe InferenceService Template](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_kserve_template) spec


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

`name` 

</td>
<td valign="top">

Parameter name

</td>
</tr>
<tr>
<td valign="top">

`default` 

</td>
<td valign="top">

\(Optional\) Default value for the parameter

</td>
</tr>
<tr>
<td valign="top">

`type` 

</td>
<td valign="top">

\(Optional\) Type of the parameter. Only “string” type is supported

</td>
</tr>
</table>



<a name="loio4d1ffd2507e94d9f8690298d88e41671__section_input_artifacts"/>

## ServingTemplate Input Artifacts

\(Appears on [ServingTemplate Spec](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_spec)\)

Input artifacts required for [KServe InferenceService Template](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_kserve_template) spec


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

`name` 

</td>
<td valign="top">

Artifact name

</td>
</tr>
</table>



<a name="loio4d1ffd2507e94d9f8690298d88e41671__section_kserve_template"/>

## KServe InferenceService Template

\(Appears on:[ServingTemplate Spec](api-schema-spec-ai-sap-com-v1alpha1-4d1ffd2.md#loio4d1ffd2507e94d9f8690298d88e41671__section_servingtemplate_spec)\)

KServe InferenceService template


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

`apiVersion`

String

</td>
<td valign="top">

KServe API version. For example, `serving.kserve.io/v1beta1`.

</td>
</tr>
<tr>
<td valign="top">

`metadata` 

</td>
<td valign="top">

Metadata for KServe InferenceService CR. See [KServe Metadata Annotations](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_kfserving_metadata_annotations) and [KServe Metadata Labels](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_kfserving_metadata_labels). Annotations and labels in metadata can be parameterized by using `{{inputs.parameters.Parameter-Name-Here}}`

</td>
</tr>
<tr>
<td valign="top">

`spec`

Multiline string

</td>
<td valign="top">

A multiline string template for [KServe InferenceServiceSpec](kserve-spec-serving-kserve-io-v1beta1-35bf43d.md#loio35bf43d700784453bd11a8c2a9125b2e__section_inferenceservicespec) with optional placeholders for parameters and artifacts

</td>
</tr>
</table>

