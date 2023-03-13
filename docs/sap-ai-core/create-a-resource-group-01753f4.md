<!-- loio01753f4dcb454401b539ecc4def641be -->

# Create a Resource Group

You can create resource groups to isolate ML workloads.

> ### Note:  
> Ids must be of length minimum: 3, maximum: 253. The first and last characters must be either a lower case letter, an upper case letter or a number. Character entries from the second to penultimate, may include a lower case letter, an upper case letter, a number, a full stop or a hyphen. No other special characters are permitted.



<a name="loio01753f4dcb454401b539ecc4def641be__section_wbq_3wg_k5b"/>

## Using Postman

1.  Create a new POST request and enter the URL `{{apiurl}}/v2/admin/resourceGroups`.
2.  As the request body, select the *raw* radiobutton and enter the following:

    ```json
    {
        "resourceGroupId": "<ID of your resource group>"
    }
    ```

    ![](images/Create_a_Resource_Group_Postman_5bcf33f.png)

3.  Send the request.

    You'll receive a 202 response to confirm that the request to create the resource group has been accepted.




<a name="loio01753f4dcb454401b539ecc4def641be__section_zbq_3wg_k5b"/>

## Using curl

1.  Create a resource group by sending the following:

    ```
    curl --location --request POST "[/pandoc/div/div/horizontalrule/orderedlist/li/codeblock/span/code
         {"filepath"}) $AI_API_URL/v2/admin/resourceGroups (code]" --header "Authorization: Bearer $TOKEN" --header 'Content-Type: application/json' --data-raw '{ "resourceGroupId": "<ID of your resource group>"}'
    
    ```


**Parent topic:** [Manage Resource Groups](manage-resource-groups-8aae6cb.md "A resource group represents a unique workspace environment, where users can create or add entities such as configurations, executions, deployments, and artifacts.")

**Related Information**  


[Create a Generic Secret](create-a-generic-secret-1831845.md "A generic secret gives SAP AI Core authorization to utilize your resource group without exposing your credentials.")

[List All Generic Secrets](list-all-generic-secrets-05a3713.md "Locate a generic secret, without revealing sensitive information.")

[Update a Generic Secret](update-a-generic-secret-b5d5970.md "Generic secrets can be amended.")

[Delete a Generic Secret](delete-a-generic-secret-d5d5187.md "Manage the lifespan of your generic secrets.")

[Consume Generic Secrets in Executions or Deployments](consume-generic-secrets-in-executions-or-deployments-185a324.md "Utilize generic secrets in executions or deployments.")

[Resource Group Level Resources](security-a476d3c.md#loiofbfa1badbbfa4981a417299238b82e39 "")

