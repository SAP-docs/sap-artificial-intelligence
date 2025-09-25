<!-- loio9555fe1f83e64aee9b12f7b7008674d6 -->

# Change Serving Template and Update Deployments

If you change a serving template, you can automatically update the deployments that are associated with that template.



<a name="loio9555fe1f83e64aee9b12f7b7008674d6__prereq_ylx_ppz_wtb"/>

## Prerequisites

The `executables.ai.sap.com/cascade-update-deployments` parameter is present and set to `true` in the serving template. This allows any change to the serving template to trigger an automatic update of the associated deployments.



## Procedure

Changes to the following are supported:

-   `spec.template.spec.default.predictor.minReplicas`
-   `spec.template.spec.default.predictor.maxReplicas`
-   `spec.template.spec.predictor.containers.image`
-   `spec.template.spec.predictor.containers.ports`
-   `spec.template.spec.predictor.containers.env`
-   Modify a value
-   Add a name-value pair
-   Parameterized values can be updated to hardcoded and vice versa

 > ### Caution:  
> The `image` parameter value can be resolved in mutltiple ways during rendering, based on priority. For more information, see [Serving Templates](serving-templates-20a8667.md).

 <a name="concept_vc4_sy2_5fc"/>

<!-- concept\_vc4\_sy2\_5fc -->

## Checking the status of updated deployments

You can check the status of the updated deployments by submitting a GET request to `{{apiurl}}/v2/lm/deployments/{{deploymentid}}`

If deployment is updated sucessfully,`lastOperation` will be updated to `"CASCADE-UPDATE"`.

```
{
    "createdAt": "2022-02-07T11:20:27+00:00",
    "deploymentUrl": "https://api.ai.devsg.eu-central-1.mlf-aws-dev.com/v2/inference/deployments/<deployment_id>",
    "executableId": "<executable_id>",
    "id": "<deployment_id>",
    "lastOperation": "CASCADE-UPDATE",
    "latestRunningTargetId": "<configuration_id>",
    "modifiedAt": "2022-02-07T11:26:10+00:00",
    "scenarioId": "<scenario_id>",
    "status": "RUNNING",
    "statusDetails": {},
    "targetId": "<configuration_id>"
}
```

