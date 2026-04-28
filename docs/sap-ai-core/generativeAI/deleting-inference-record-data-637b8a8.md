<!-- loio637b8a8d654e42c3b1202f3ba0ae083b -->

# Deleting Inference Record Data

Deletion of inference record data includes all of metadata and labels, but not the request, response, or feedback.



## Prerequisites

-   You've made a request to an LLM or orchestration, and included inference recording in your headers. For more information, see [Record an Inference in Inference Observability](record-an-inference-in-inference-observability-7d493c7.md).
-   You know the ID of the inference record that you want to access, or you've included labels in your record. For more information, see [Record an Inference in Inference Observability](record-an-inference-in-inference-observability-7d493c7.md) and [Adding to an Inference Record](adding-to-an-inference-record-e57dbe5.md).

Ensure that you have the following headers set:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

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
</table>



## Context

> ### Note:  
> If no selection criteria are provided, all inference record data for the specific resource group will be deleted.

The API supports bulk deletion of all objects that fit your selection criteria.

You can specify a time-frame and label selection criteria.

> ### Caution:  
> Data stored in the S3 data store such as request, response, and feedback, is not deleted. It is your responsibility to delete the data from the S3 store.



## Procedure

1.  Send a POST request to the endpoint: `$AI_API/observability/inferencesDeleteRequests`. Include your selection criteria in the body.

    The following example shows a request for deletion of data associated with `key`: *<medium\>* and `value`: *<mobile\>*, created within a specific time-frame:

    > ### Sample Code:  
    > ```
    > curl --request POST \
    >   --url $AI_API/observability/inferencesDeleteRequests \
    >   --header 'ai-resource-group: <resource_group>' \
    >   --header 'authorization: Bearer $TOKEN' \
    >   --header 'content-encoding: application/json' \
    >   --header 'content-type: application/json' \
    >   --data '  {
    >     "startTime": "2026-03-16T10:22:23.012Z",
    >     "endTime": "2026-03-17T10:22:23.012Z",
    >     "labelSelectors": [
    >       {
    >         "key": "ext.ai.sap.com/medium",
    >         "value": "mobile"
    >       }
    >     ]
    >   }'
    > 
    > ```

    The response includes the ID of the delete request.

    > ### Output Code:  
    > ```
    > {
    >   "id": "74d5227a-fb5e-4fae-82cb-3b4f77b7a6b9"
    > }
    > ```

2.  Use the ID of the delete request to check the status of the delete request.

> ### Sample Code:  
> ```
> curl --request GET \
>   --url $AI_API/observability/inferencesDeleteRequests/{{inferencesDeleteRequestId}} \
>   --header 'ai-resource-group: <resource_group>' \
>   --header 'authorization: Bearer $TOKEN' \
>   --header 'content-encoding: application/json'
> ```



## Results

Responses include a success message and a confirmation of the criteria used for deletion.

> ### Output Code:  
> ```
> 
> {
>   "status": "COMPLETED",
>   "filters": {
>     "labelSelectors": [
>       {
>         "key": "ext.ai.sap.com/medium",
>         "value": "mobile"
>       }
>     ],
>     "startTime": "2026-03-16T10:22:23.012Z",
>     "endTime": "2026-03-17T10:22:23.012Z"
>   },
>   "submittedAt": "2026-03-17T10:37:25.2043074Z",
>   "completedAt": "2026-03-17T10:40:06.5120414Z"
> }
> ```

