<!-- loio05a3713aa6a94356b08e09e86260b16d -->

# List All Generic Secrets

Locate a generic secret, without revealing sensitive information.

To list generic secrets belonging to a particular resource group, use the GET endpoint as shown below. The response includes a list of generic secrets, their name, and their creation timestamp. No sensitive information is revealed in the response.



<a name="loio05a3713aa6a94356b08e09e86260b16d__section_vtj_nwk_4rb"/>

## Using Postman

1.  Create a GET request and enter the URL `{{apiurl}}/v2/admin/secrets`.
2.  As the request body, select the *none* radiobutton.
3.  Specify the scope of the request via the header `AI-Tenant-Scope` or `AI-Resource-Group`:
    -   ***AI-Tenant-Scope*** : ***true***. The operation will be performed at the main tenant level.
    -   ***AI-Resource-Group*** : ****<resource-group-name\>****. The operation will be performed at the resource-group level.

4.  Send the request.

![](images/List_Generic_Secrets_in_Postman_7de47dd.png)



<a name="loio05a3713aa6a94356b08e09e86260b16d__section_mkn_wwk_4rb"/>

## Using curl

Submit a GET request to the endpoint `/v2/admin/secrets`, using the resource-group scope. For the main-tenant scope level, replace the last header with `AI-Tenant-Scope: true`.

```
curl --location --request GET "[/pandoc/div/div/horizontalrule/codeblock/span/code
     {"filepath"}) $AI_API_URL/v2/admin/secrets (code]" \
--header "Authorization: Bearer $TOKEN" \
--header 'AI-Resource-Group: default'

```

**Parent topic:** [Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group represents a unique workspace environment, where users can create or add entities such as configurations, executions, deployments, and artifacts.")

**Related Information**  


[Create a Resource Group](create-a-resource-group-01753f4.md "You can create resource groups to isolate ML workloads.")

[Create a Generic Secret](create-a-generic-secret-1831845.md "A generic secret gives SAP AI Core authorization to utilize your resource group without exposing your credentials.")

[Update a Generic Secret](update-a-generic-secret-b5d5970.md "Generic secrets can be amended.")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "Manage the lifespan of your generic secrets.")

[Consume Generic Secrets in Executions or Deployments](consume-generic-secrets-in-executions-or-deployments-185a324.md "Utilize generic secrets in executions or deployments.")

