<!-- loiod029a32c22fb45fbb607e6a2c48c8a0e -->

# What Is SAP AI Core?

Learn more about the SAP AI Core service on SAP Business Technology Platform \(SAP BTP\).

SAP AI Core is a service in the SAP Business Technology Platform that is designed to handle the execution and operations of your AI assets in a standardized, scalable, and hyperscaler-agnostic way. It provides seamless integration with your SAP solutions. Any AI function can be easily realized using open-source frameworks. SAP AI Core supports full lifecycle management of AI scenarios. Access generative AI capabilities and prompt lifecycle management via the generative AI hub.

SAP AI Core allows you to make data driven decisions confidently and efficiently, and is tailored to business problems. It handles large volumes of data and provides scalable machine learning capability, to automate tasks such as triage services for customer feedback or tickets and classification tasks. SAP AI Core comes with preconfigured SAP solutions, can be configured for open source machine learning frameworks, can be used with Argo Workflow and KServe, and can be embedded into other applications.

SAP AI Core allows you to experiment with and utilize natural language prompts with a variety of generative AI models in the Generative AI Hub.

> ### Tip:  
> The English version of this guide is open for contributions and feedback using GitHub. This allows you to get in contact with responsible authors of SAP Help Portal pages and the development team to discuss documentation-related issues. To contribute to this guide, or to provide feedback, choose the corresponding option on SAP Help Portal:
> 
> -   *Feedback* \> *Create issue*: Provide feedback about a documentation page. This option opens an issue on GitHub.
> 
> -   *Feedback* \> *Edit page*: Contribute to a documentation page. This option opens a pull request on GitHub.
> 
> 
> You need a GitHub account to use these options.
> 
> More information:
> 
> -   [Contribution Guidelines](https://help.sap.com/docs/open-documentation-initiative/contribution-guidelines/readme.html)
> 
> -   [Introduction Video](https://www.youtube.com/watch?v=WJ0oarMlVW4)
> 
> -   [Introduction Blog Post](https://blogs.sap.com/2021/11/29/sap-btp-documentation-goes-github-new-collaboration-process/)



<a name="loiod029a32c22fb45fbb607e6a2c48c8a0e__section_cfb_tt3_snb"/>

## Environment

This service runs in the following environments:

-   Cloud Foundry
-   Kyma
-   Kubernetes



<a name="loiod029a32c22fb45fbb607e6a2c48c8a0e__section_a51_2xm_vzb"/>

## Multitenancy

This service supports multitenancy. It can be used in tenant-aware applications.



<a name="loiod029a32c22fb45fbb607e6a2c48c8a0e__section_efb_tt3_snb"/>

## Features


<dl>
<dt><b>

Execute pipelines 

</b></dt>
<dd>

Execute pipelines as a batch job, for example, to preprocess or train your models, or perform batch inference.



</dd><dt><b>

Serve inference requests 

</b></dt>
<dd>

Deploy а trained machine learning model as a Web service to serve inference requests of trained models with high performance.



</dd><dt><b>

Manage the AI scenario lifecycle 

</b></dt>
<dd>

Manage your ML artifacts and workflows, such as model training, metrics tracking, data, models, and model deployments via a uniform API lifecycle.



</dd><dt><b>

Benefit from multitenancy support 

</b></dt>
<dd>

Use this service in tenant-aware applications. Implement multi-tenant services to segregate your AI assets and executions to isolate your tenants within SAP AI Core.



</dd><dt><b>

Integrate your cloud infrastructure 

</b></dt>
<dd>

Register your Docker registry, synchronize your AI content from your git repository, and register your object store for training data and trained models. Productize your AI content and expose it as a service to consumers in the SAP BTP marketplace.



</dd><dt><b>

Generative AI hub 

</b></dt>
<dd>

Choose from a selection of generative AI models for prompt experimentation, and prompt lifecycle management.



</dd>
</dl>



<a name="loiod029a32c22fb45fbb607e6a2c48c8a0e__section_jq4_gpf_4rb"/>

## Process Flow Between SAP AI Core and SAP AI Launchpad

![](images/Process_Flow_AI_Launchpad_to_AI_Core_d8dde1d.png)

**Related Information**  


[AI API Overview](ai-api-overview-716d4c3.md "The AI API lets you manage your AI assets (such as training scripts, data, models, and model servers) across multiple runtimes.")

[SAP AI Launchpad](https://help.sap.com/ailaunchpad)

