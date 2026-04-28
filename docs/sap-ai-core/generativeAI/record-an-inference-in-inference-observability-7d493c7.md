<!-- loio7d493c7a77cb44a8a7d9897e177abdd1 -->

# Record an Inference in Inference Observability



## Prerequisites

-   You're using the extended service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right:.

-   If you want to store your request, response, and feedback data: you’ve registered an object store secret. For more information, see [Register an Object Store for Inference Observability](register-an-object-store-for-inference-observability-babcd84.md).

-   You have a running orchestration or model deployment in the target resource group. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md) or [Foundation Models](foundation-models-2d981fb.md).




## Procedure

To access generative AI models, send a request to an inference endpoint. For more information, see [Orchestration Workflow V2](orchestration-workflow-v2-41a0247.md) or [Consume Models](consume-models-bf0373b.md).

To record your inference, you must include the following headers in your request:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`ai-inference-observability-persistence-mode`

</td>
<td valign="top">

Choose from the following:

-   `full`: stores the request and response payload, including the metadata.
-   `metadata`: metadata only.

> ### Note:  
> If you want to store feedback, you have to set `ai-inference-observability-persistence-mode` headers to `full`.



</td>
</tr>
<tr>
<td valign="top">

`ai-object-store-secret-name`

</td>
<td valign="top">

Required for requests with `full` persistence mode. Not required for `metadata` persistence mode.

The object store secret name where your request and response payloads should be saved.

</td>
</tr>
<tr>
<td valign="top">

`ai-inference-observability-labels`

</td>
<td valign="top">

Optional

Extra labels that will be attached to the metadata for later filtering.

The following conditions apply:

-   Maximum of 16 labels

-   Comma-separated list of key-value pairs.

-   The key must use prefix `ext.ai.sap.com` 

-   Maximum length of key and value: 64 characters.

-   Only uppercase and lowercase ASCII letters, numbers and the characters “-”, “.”, and “ /” are permitted.


Example value: `ext.ai.sap.com/env=prod,ext.ai.sap.com/team=ml`

</td>
</tr>
</table>

> ### Note:  
> Only inferences sent to orchestration or foundation models are recorded.



## Results

Requests sent with `ai-inference` headers automatically record either the metadata or request, response payload, and metadata, depending on the selected mode.

The response includes an inference ID that can be used to access inference observability.



## Next Steps

You can use your inference ID to:

-   Store additional labels and feedback

-   Retrieve the metadata and the request, response, and feedback \(if stored\).


