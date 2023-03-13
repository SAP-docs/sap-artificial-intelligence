<!-- loio442a7e89136541c6bbd36c4177db8379 -->

# Templates

As an AI scenario consumer, you subscribe to an AI service. The AI service comes with predefined scenarios which contain templates.

A scenario consists of templates for the same use case. A template is an AI pipeline for a use case. A pipeline can be used to train a model, or to deploy a model.

A template consists of code that defines the components that are required for the AI pipeline.

Templates define placeholders for parameters, inputs \(such as datasets\), and outputs \(such as models\). You can use any dataset as template input, provided it has the required structure. User-defined labels can be applied to a template and are listed with the template’s details.

A configuration helps you attach values to the placeholders for the template. You can create multiple configurations for the same template.

There are two types of template; run template and deployment template.

-   A template that is used to train a model is called a run template. An instance of a run template is a run. Runs generate output, such as models.

-   A template that is used to deploy a model is called a deployment template. An instance of deployment template is a deployment. Deployments generate URLs that can be used for inference.


To use a template, you must create its instance \(either a run or a deployment\) and associate with a configuration \(data\).

> ### Note:  
> Templates are re-usable. The same template can be used for either training or deploying a model.

> ### Example:  
> Consider a scenario, such as a product review classification \(involving positive or negative reviews\). The run template ***Product\_Review\_Training*** has placeholders, as follows:
> 
> Input parameters:
> 
> -   `Num_of_epochs`
> 
> -   `Max_Depth_Decision_Tree`
> 
> Input \(datasets\):
> 
> -   `Stopwords_Dataset`
> 
> -   `Past_Reviews_Dataset` 

The following types of template are available in a scenario for AI scenario consumers:

-   **[Run Templates](run-templates-febb85e.md "A template that is used to train an AI model is called a run template
		.")**  
A template that is used to train an AI model is called a run template .
-   **[Deployment Templates](deployment-templates-d180ad2.md "A deployment template is used to deploy an AI model.")**  
A deployment template is used to deploy an AI model.

