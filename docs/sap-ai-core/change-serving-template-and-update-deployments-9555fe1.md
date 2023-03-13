<!-- loio9555fe1f83e64aee9b12f7b7008674d6 -->

# Change Serving Template and Update Deployments

If you change a serving template, you can automatically update the deployments that are associated with that template.



<a name="loio9555fe1f83e64aee9b12f7b7008674d6__prereq_ylx_ppz_wtb"/>

## Prerequisites

The `executables.ai.sap.com/cascade-update-deployments` parameter is present and set to ***true*** in the serving template. This allows any change to the serving template to trigger an automatic update of the associated deployments.



## Procedure

1.  Make any required changes to the fields for the serving template. Changes to the following are supported:

    -   `spec.template.spec.default.predictor.minReplicas`
    -   `spec.template.spec.default.predictor.custom.container.image`
    -   `spec.template.spec.default.predictor.custom.container.ports`
    -   `spec.template.spec.default.predictor.custom.container.env`

2.  Make any required changes to the fields for the beta serving template. Changes to the following are supported:

    -   `spec.template.spec.predictor.containers.image`
    -   `spec.template.spec.predictor.containers.ports`
    -   `spec.template.spec.predictor.containers.env`
    -   Modify a value
    -   Add a name-value pair
    -   Parameterized values can be updated to hardcoded and vice versa


