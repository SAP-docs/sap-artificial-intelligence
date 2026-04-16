<!-- copy306fea4133e445839e8e5d34f55070ff -->

# Create a Pipeline with SAP Document Management Service



<a name="copy306fea4133e445839e8e5d34f55070ff__section_ljc_ksf_ngc"/>

## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   You have created a generic secret. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).
-   You've added your grounding documents to your document store and you're using a supported data source and document type. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).



<a name="copy306fea4133e445839e8e5d34f55070ff__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines`.


The following shows an example of a SAP Document Management service site to be indexed.

Populate the sample code with the following values:


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

\{\{resource\_group\}\}

</td>
<td valign="top">

The AI resource group assigned to your account

</td>
</tr>
<tr>
<td valign="top">

$AI\_API\_URL

</td>
<td valign="top">

The base URL of your SAP AI Core environment. This can also be set as an environment variable.

</td>
</tr>
<tr>
<td valign="top">

\{\{access\_token\}\}

</td>
<td valign="top">

Your access token for SAP AI Core

</td>
</tr>
<tr>
<td valign="top">

<generic secret name\> \(destination\)

</td>
<td valign="top">

The name of the generic secret created for SAP Document Management service

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines \
>   --header 'AI-Resource-Group: {{resource_group}}' \
>   --header 'Content-Type: application/json' \ 
>   --header 'Authorization: Bearer {{access_token}}'
>   --data '{
>   "type": "SDM",
>   "metadata": {
>     "destination": "<generic secret name>"
>   }
> }'
> ```



### Scheduling updates

Optionally, you can add a `configuration` containing a `cronExpression` to schedule updates to your pipeline, at intervals of your choice.

For more information, see [Cron Expressions](cron-expressions-6175008.md).

For example:

```
curl --request POST \
  --url $AI_API_URL/v2/lm/document-grounding/pipelines \
  --header 'AI-Resource-Group: {{resource_group}}' \
  --header 'Content-Type: application/json' \ 
  --header 'Authorization: Bearer {{access_token}}'
  --data '{
    "type": "SDM",
    "metadata": {
        "destination": "sdm-secret-aicore"
    },
    "configuration": {
        "cronExpression": "<cron expression>"
    }
}'
```

> ### Note:  
> Each repetition of your pipeline is a new deployment, and incurs costs.



<a name="copy306fea4133e445839e8e5d34f55070ff__section_c2d_1wg_jgc"/>

## Next Steps

After preparing your vectors, you can use the Retrieval API for chunks relevant to a query, or use the grounding module as part of an orchestration workflow for information retrieval and LLM interaction. For more information, see [Retrieval API](retrieval-api-281e8cf.md) or [Using the Grounding Module](using-the-grounding-module-e1c4dd1.md).

