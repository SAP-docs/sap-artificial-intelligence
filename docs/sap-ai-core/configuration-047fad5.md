<!-- loio047fad5d55ed4e76a7930a11ae70d7bb -->

# Configuration



<a name="loio047fad5d55ed4e76a7930a11ae70d7bb__section_oqs_yqk_vsb"/>

## Could not create configuration, because executable *<x\>* for scenario *<y\>* is not found

When you try to create a configuration, you are told that an executable cannot be found for your scenario.



### Check the following:

1.  Check that you are using the `name` value from your workflow for the executable ID in the configuration.

    ```
    apiVersion: argoproj.io/v1alpha1
    kind: WorkflowTemplate
    metadata:
    		name: text-clf-train-tutorial
    		annotations:
    			scenarios.ai.sap.com/description: "SAP developers tutorial scenario"
    ...
    ```

    > ### Note:  
    > Do not use the value from `executables.ai.sap.com/id` as an executable ID.

2.  Check that you are using the value of `executables.ai.sap.com/id` from your workflows as your scenario ID.

    ```
    ...
    		artifacts.ai.sap.com/text-data.kind: "dataset"
    		artifacts.ai.sap.com/text-model-tutorial.kind: "model"
    	labels:
    		scenarios.ai.sap.com/id: "text-clf-tutorial"
    		ai.sap.com/version: "2.1.0"
    	spec:
    ...
    ```




<a name="loio047fad5d55ed4e76a7930a11ae70d7bb__section_vxt_yqk_vsb"/>

## Log message: using minio client



### Check the following:

1.  Check that you are using the `name` value from your workflow for the executable ID in the configuration.

    ```
    apiVersion: argoproj.io/v1alpha1
    kind: WorkflowTemplate
    metadata:
    		name: text-clf-train-tutorial
    		annotations:
    			scenarios.ai.sap.com/description: "SAP developers tutorial scenario"
    ...
    ```

    > ### Note:  
    > Do not use the value from `executables.ai.sap.com/id` as an executable ID.

2.  Check that you are using the value of `executables.ai.sap.com/id` from your workflows as your scenario ID.

    ```
    ...
    		artifacts.ai.sap.com/text-data.kind: "dataset"
    		artifacts.ai.sap.com/text-model-tutorial.kind: "model"
    	labels:
    		scenarios.ai.sap.com/id: "text-clf-tutorial"
    		ai.sap.com/version: "2.1.0"
    	spec:
    ...
    ```


**Parent topic:**[Troubleshooting](troubleshooting-3da90ba.md "For troubleshooting information, see the following sections:")

**Related Information**  


[Repository](repository-fcad603.md "")

[Artifacts](artifacts-c655daa.md "")

[Application](application-7f1e35b.md "")

[Execution](execution-5ccde4d.md "")

[Docker](docker-1945aa4.md "")

[Deployment](deployment-a10fa8a.md "")

[Miscellaneous](miscellaneous-10622b5.md "")

