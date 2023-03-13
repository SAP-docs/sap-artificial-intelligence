<!-- loio05f41ee00e634e958cddd5e38e31569f -->

# Terminology




<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Definition



</th>
</tr>
<tr>
<td valign="top">

AI API



</td>
<td valign="top">

An essential API that handles all AI artifacts and workflows \(such as training scripts, data, models, and model servers\) across multiple AI runtimes.



</td>
</tr>
<tr>
<td valign="top">

Artifact



</td>
<td valign="top">

A reference to data or a file that is produced or consumed by an execution or deployment.



</td>
</tr>
<tr>
<td valign="top">

Configuration



</td>
<td valign="top">

A collection of parameters, artifact references, and executables that is used to run an execution or deployment. A configuration is required to instantiate an execution. Executables and configurations have a 1:n relationship \(that is, one executable can have many configurations\).



</td>
</tr>
<tr>
<td valign="top">

Dataset



</td>
<td valign="top">

A type of artifact. A dataset references a data source and the instruments required to access and investigate it.

A dataset:

-   References an acquired dataset on a data plane or an application API

-   Can be passed as a dataset artifact to a scenario at runtime



</td>
</tr>
<tr>
<td valign="top">

Deployment



</td>
<td valign="top">

A deployment is an instance of a model serving template that is configured to use a `model` type artifact and to apply it to data passed in a serving request \(for example, for a prediction\).

Once a deployment has been instantiated successfully, a model server is created and a deployment URL is generated for inference. As input, the deployment takes one or more models and the parameters from a configuration.



</td>
</tr>
<tr>
<td valign="top">

Executable



</td>
<td valign="top">

An executable is a template that is instantiated for a purpose, such as training a model or creating a deployment

User-defined labels can be applied to an executable and are listed with the executable's details.

-   If a nondeployable executable is instantiated, it results in an execution. Executions may produce output artifacts

-   If a deployable executable is instantiated, it results in a deployment. Deployments generate URLs that can be used for inference




</td>
</tr>
<tr>
<td valign="top">

Execution



</td>
<td valign="top">

An execution is an instance of a non-deployable executable. Executions are used to train a model or to run other types of workflow.

An execution runs only once and produces an output artifact. If a training instance is executed, the output artifacts produced are models.

There is typically a large amount of metadata associated with an execution. The metadata is stored as metrics \(and associated labels\), tags, and custom info. Multiple metrics, tags and custom info can be passed with a single execution.

Once the metric, tag and custom info are saved, they can be queried with an *<execution ID\>*.

Every metric, tag and custom info must be associated with an execution.



</td>
</tr>
<tr>
<td valign="top">

Workflow executable



</td>
<td valign="top">

A workflow executable is used within the *ML Operations* application.

A workflow executable defines a set of parameters and the input artifacts that it needs to be instantiated. These are provided by a configuration. The workflow executable also defines a set of output artifacts that would be generated if the executable were to be instantiated and run successfully.



</td>
</tr>
<tr>
<td valign="top">

Job executable



</td>
<td valign="top">

A job executable is a simplified representation of a workflow executable that is used within the *Functions Explorer* application.



</td>
</tr>
<tr>
<td valign="top">

Job template



</td>
<td valign="top">

A type of executable in SAP AI Core that specifies a long-running process, typically a training or batch inference.



</td>
</tr>
<tr>
<td valign="top">

Model



</td>
<td valign="top">

A type of artifact that is the output of training.



</td>
</tr>
<tr>
<td valign="top">

Model serving template



</td>
<td valign="top">

A type of executable in SAP AI Core that specifies how a model is to be served.



</td>
</tr>
<tr>
<td valign="top">

Operations



</td>
<td valign="top">

All activities within the AI lifecycle such as executing trainings, creating model deployments, application integration, and model monitoring.



</td>
</tr>
<tr>
<td valign="top">

Resource group



</td>
<td valign="top">

A resource group represents a unique workspace created for an SAP AI Core scenario consumer and for a unique purpose. A resource group requires a valid subscription to a tenant.

Within a resource group, users create or add entities such as configurations, executions, deployments, and artifacts. They consume the executables that are available in the scenarios.

Before users can instantiate an executable, they must create a configuration.

-   If a nondeployable executable is instantiated, it results in an execution. Executions optionally produce output artifacts.

-   If a deployable executable is instantiated, it results in a deployment. Deployments generate URLs that can be used for inference.




</td>
</tr>
<tr>
<td valign="top">

Runtime



</td>
<td valign="top">

A platform that offers processing resources to execute AI learning loads, such as training and inference.



</td>
</tr>
<tr>
<td valign="top">

 SAP AI Core 



</td>
<td valign="top">

An infrastructure that enables a customer's business applications to become intelligent with AI and machine learning technology, and their data to train AI services to help automate tasks and processes.



</td>
</tr>
<tr>
<td valign="top">

Scenario



</td>
<td valign="top">

 A scenario is a group of related executables for a use case within the user's tenant. A scenario can have multiple versions that further correspond to the different versions of executables. 



</td>
</tr>
<tr>
<td valign="top">

Serving executable



</td>
<td valign="top">

A serving executable is a deployable template pipeline that can be instantiated to create a deployment.

A serving executable defines a set of parameters and the input artifacts that it needs to be instantiated; these are provided by a configuration.



</td>
</tr>
<tr>
<td valign="top">

Training



</td>
<td valign="top">

An execution or executable that produces \(at least\) an artifact of type `model`.



</td>
</tr>
</table>

**Parent topic:** [Concepts](concepts-4c6b2da.md "In this section, we'll explore some of the concepts surrounding SAP AI Core.")

**Related Information**  


[SAP AI Core Overview](sap-ai-core-overview-88e0078.md "SAP AI Core is the key to integrating artificial intelligence capabilities in your SAP solutions.")

[Overview of SAP AI Core Systems](overview-of-sap-ai-core-systems-c243d2a.md "Your SAP AI Core system connects internal and external tools.")

[Resource Groups](resource-groups-26c6c6b.md#loio26c6c6b50e3f412f8bc0cd6a8ebdb850 "SAP AI Core tenants use resource groups to isolate related ML resources and workloads. Scenarios, executables, and Docker registry secrets are shared across all resource groups.")

