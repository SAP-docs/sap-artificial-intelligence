<!-- loio3c9d504720d8491d8955c0ae8cb81e54 -->

# Configurations

Configurations combine artifacts \(such as datasets or models\) with executables, so that training or deployment processes can be undertaken.

Configurations combine the following:

-   Executables and scenarios

    Executables and scenarios include the specific version of the AI pipeline template that is used to train or deploy an AI use case. They contain placeholders for artifacts and parameters.

-   Artifacts

    Artifacts are either datasets \(used for training\), or models \(used for deployment\). Artifacts fill the placeholders in an executable \(input artifacts and output artifacts\).

-   Parameters \(manually supplied\)

    Parameters are alphanumeric values that are used mostly for hyperparameters. Hyperparameters are variables that change a model's decision-making capabilities. They are used to fill the placeholders in an executable.


You can create multiple configurations using the same or different values. After you have defined your configuration and defined the values, you can start the process of training or deployment.

Configurations can be reused in multiple executions, where data `kinds` match.

-   **[View a Configuration](view-a-configuration-d3de4a4.md "A configuration consists of parameters and input artifact references for training or deployment processes.")**  
A configuration consists of parameters and input artifact references for training or deployment processes.
-   **[Create a Configuration](create-a-configuration-03bdcc7.md "A configuration combines parameters, artifacts (for example, a dataset or model), and executables, that are used in training or deploying
		a model.")**  
A configuration combines parameters, artifacts \(for example, a dataset or model\), and executables, that are used in training or deploying a model.

**Related Information**  


[Executables](executables-06f4794.md "An executable is used to define training or serving pipelines for an AI use case. Executables for the same AI use case are grouped by scenario.")

[Datasets](datasets-e299ed5.md "A dataset is a type of artifact which is registered in your AI runtime. A registered dataset references files that are stored in your connected hyperscaler object store.")

[Models](models-aba8797.md "A model is a type of artifact that results from a training process.")

