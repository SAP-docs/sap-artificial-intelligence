<!-- loiob7dc8b48df2b4f009e9157f5448c7935 -->

# Build Your Orchestration Workflow

You build your orchestration workflow by designing and testing a prompt that can be populated with different data during inference.



## Prerequisites

-   You have an orchestration deployment running. For more information, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4344c5b.md).

-   You have the role `orchestration_executor`, `genai_experimenter`, or `genai_manager`, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).




<a name="loiob7dc8b48df2b4f009e9157f5448c7935__context_a51_5qc_ybc"/>

## The Orchestration Workflow

Navigate to the landing page for orchestration by choosing *Generative AI Hub* \> *Orchestration* and clicking *Create*. SAP AI Launchpad displays the following workflow, which you can use to build your orchestration.

In a basic orchestration scenario, you can combine different modules from orchestration into a pipeline that can be executed with a single API call. Within the pipeline, the response from one module is used as the input for the next module.

The order in which the pipeline is executed is defined centrally in orchestration. However, you can configure the details for each module and omit optional modules by passing an orchestration configuration in JSON format with the request body.

**The image below is interactive. Click each part of the workflow for more information.**

![](images/4a_orchstration_workflow_2083f88.png)

-   [Grounding](grounding-2d495d3.md)
-   [Templating](templating-11d44e6.md)
-   [Input Translation](input-translation-7ff3489.md)
-   [Data Masking](data-masking-79911bd.md)
-   [Input Filtering](input-filtering-f5c7223.md)
-   [Model Configuration](model-configuration-be3cd61.md)
-   [Output Filtering](output-filtering-32a0e42.md)
-   [Output Translation](output-translation-e350c56.md)



<a name="loiob7dc8b48df2b4f009e9157f5448c7935__section_xjc_nzr_dcc"/>

## Editing the Orchestration Workflow

You can change the orchestration workflow by showing or hiding modules. To do so, click the *Edit* button and toggle the switch to show or hide the modules as required. Note that you can only hide optional modules.

> ### Restriction:  
> Templating and Model Configuration modules are mandatory and therefore can't be hidden.



<a name="loiob7dc8b48df2b4f009e9157f5448c7935__section_rkz_zmx_dcc"/>

## Uploading an Orchestration Workflow

You can upload your own orchestration workflow in JSON format. The workflow structure must match the following example:

```json
{
    "module_configurations": {
        "llm_module_config": {
            "model_name": "gpt-35-turbo",
            "model_params": {},
            "model_version": "0613"
        },
        "templating_module_config": {
            "template": [
			{
                    "role": "user",
                    "content": "what is {{?context}} ?"
               }
		],
            "defaults": {
                "context": "artificial intelligence"
            }
        },
        "filtering_module_config": {
            "input": {
                "filters": [
                    {
                        "type": "azure_content_safety",
                        "config": {
                            "Hate": "2",
                            "SelfHarm": "2",
                            "Sexual": "2",
                            "Violence": "2"
                        }
                    }
                ]
            },
            "output": {
                "filters": [
                    {
                        "type": "azure_content_safety",
                        "config": {
                            "Hate": "2",
                            "SelfHarm": "2",
                            "Sexual": "2",
                            "Violence": "2"
                        }
                    }
                ]
            }
        }
    }
}
```

> ### Restriction:  
> Orchestration workflows containing images can be downloaded in JSON format, but cannot be uploaded.

1.  Click *JSON* to show the JSON file for your orchestration workflow.

2.  Click *Upload* to upload your edited JSON file.

    The size of your file cannot exceed 200 KB.

3.  If necessary, you can download the JSON file again by clicking *Download*.


> ### Note:  
> If the parameters in your uploaded JSON are invalid to the selected model, they will be ignored.

-   **[Grounding](grounding-2d495d3.md "")**  

-   **[Templating](templating-11d44e6.md "")**  

-   **[Input Translation](input-translation-7ff3489.md "")**  

-   **[Data Masking](data-masking-79911bd.md "The data masking module is optional and serves to anonymize or pseudonymize personally
		identifiable information from the input for selected entities.")**  
The data masking module is optional and serves to anonymize or pseudonymize personally identifiable information from the input for selected entities.
-   **[Input Filtering](input-filtering-f5c7223.md "")**  

-   **[Model Configuration](model-configuration-be3cd61.md "")**  

-   **[Output Filtering](output-filtering-32a0e42.md "")**  

-   **[Output Translation](output-translation-e350c56.md "")**  


