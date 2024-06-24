<!-- loioc243d2aa9dee43a5b15ed9c96f55f152 -->

# SAP AI Core Systems Overview

Your SAP AI Core system connects internal and external tools.

Users interact with the various repositories, systems, and objects when working with SAP AI Core; some of these objects are provided by SAP. In other cases, customers provide these components to enable enhanced control \(authorizations\) and continuous integration/continuous deployment \(CI/CD\).



<a name="loioc243d2aa9dee43a5b15ed9c96f55f152__section_vk1_mhl_kqb"/>

## Key Repositories, Systems, and Objects

**Summary of Elements and Their Use**


<table>
<tr>
<th valign="top">

What

</th>
<th valign="top">

Why

</th>
</tr>
<tr>
<td valign="top">

Git repo

</td>
<td valign="top">

For storing training and serving workflows and templates

</td>
</tr>
<tr>
<td valign="top">

Hyperscaler storage

</td>
<td valign="top">

For storage of input and output artifacts, such as training data and models \(for example, SAP BTP Object Store Service\)

</td>
</tr>
<tr>
<td valign="top">

Docker repo

</td>
<td valign="top">

For custom Docker images referenced in the templates

</td>
</tr>
<tr>
<td valign="top">

Kubernetes \(K8s\)

</td>
<td valign="top">

The K8s cluster orchestrates and scales the pods, which are used in AI pipelines. Resource group isolation is based on a K8s namespace.

</td>
</tr>
<tr>
<td valign="top">

KServing \(K\)

</td>
<td valign="top">

For optimized deployments of machine learning models. Deployment templates use KServe notation.

</td>
</tr>
<tr>
<td valign="top">

AI API

</td>
<td valign="top">

For managing your artifacts and workflows \(such as training scripts, data, models, and model servers\) across multiple runtimes

> ### Note:  
> The AI API can also be used to integrate other machine learning platforms, engines or runtimes into the AI ecosystem.



</td>
</tr>
<tr>
<td valign="top">

Argo Workflows

</td>
<td valign="top">

A container native, workflow engine for Kubernetes.

</td>
</tr>
<tr>
<td valign="top">

SAP AI Launchpad

</td>
<td valign="top">

SAP AI Launchpad is a multitenant software as a service \(SaaS\) application on SAP Business Technology Platform \(SAP BTP\). Customers and partners can use SAP AI Launchpad to manage AI use cases \(scenarios\) across multiple instances of AI runtimes \(such as SAP AI Core\). SAP AI Launchpad also provides generative AI capabilities via the Generative AI Hub.

</td>
</tr>
</table>



<a name="loioc243d2aa9dee43a5b15ed9c96f55f152__section_g5q_dhl_kqb"/>

## Synchronization

-   Your GitOps implementation is integrated with SAP AI Core to enable CI/CD.

-   Templates are synchronized from your Git repository to a Kubernetes cluster.

-   Your training and serving templates are regularly synchronized \(every few minutes\).

-   SAP AI Core checks the template syntax, and if synchronization fails, then error messages are displayed.


![](images/Image_AIF_Ecosystem_sync_1ec02f9.png)

![](images/ai_core_process_summary_55e1a19.png)

![](images/aI_core_flow_2529212.png)



<a name="loioc243d2aa9dee43a5b15ed9c96f55f152__section_igm_qgl_kqb"/>

## Process Summary

-   An SAP BTP token is used in `AI API` for authentication of the API calls.

-   Users run templates via the AI API.

-   Training templates are executed using the Argo workflow. The training pipeline consumes data input artifacts and outputs a model artifact.

-   An execution is created using the training template and AI API configuration. The result is a training job.

-   Serving templates are deployed using KServing.

-   A deployment is created using the serving template and AI API configuration. The result is an inference server.
-   Artifacts \(such as datasets, models\) are copied to and from the hyperscaler storage.

-   Required images are pulled from the registered Docker repository.

-   Details about scenarios and executables are retrieved from the Kubernetes cluster by the `AI API`.


![](images/ai_core_git_ops_599438b.png)

