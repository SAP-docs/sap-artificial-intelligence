<!-- loio51a3fe16807a4ed09704aa3097fe994e -->

# Create a Metadata Configuration

Creates a new metadata configuration and triggers document enumeration for the configured repository.



## Context

You can create a metadata configuration for reuse across your pipelines, instead of defining a metadata configuration for each pipeline.



<a name="loio51a3fe16807a4ed09704aa3097fe994e__section_ljc_ksf_ngc"/>

## Prerequisites

-   You have created a resource group. For more information, see [Create a Resource Group for Grounding](create-a-resource-group-for-grounding-e32efa5.md).
-   You have created a generic secret. For more information, see [Generic Secrets for Grounding](generic-secrets-for-grounding-e1a201c.md).
-   You've added your grounding documents to your document store and you're using a supported data source and document type. For more information, see [Pipelines API](pipelines-api-d8cc0e3.md).



<a name="loio51a3fe16807a4ed09704aa3097fe994e__section_vcb_j5f_ngc"/>

## Procedure

1.  Send a POST request to the endpoint `$AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations`.


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

name

</td>
<td valign="top">

A unique identifier for your configuration

</td>
</tr>
<tr>
<td valign="top">

destinationName

</td>
<td valign="top">

The name of the generic secret for your data repository

</td>
</tr>
<tr>
<td valign="top">

dataRepositoryType

</td>
<td valign="top">

Your data repository type. Choose from:

-   `MSSharePoint`
-   `S3`
-   `SFTP`



</td>
</tr>
<tr>
<td valign="top">

includePaths

</td>
<td valign="top">

The paths to the documents to be included, in a comma separated list.

</td>
</tr>
<tr>
<td valign="top">

labels

</td>
<td valign="top">

Your metadata labels in key-value pairs.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> curl --request POST \
>   --url $AI_API_URL/v2/lm/document-grounding/pipelines/metadata/configurations \
>   --header 'AI-Resource-Group: <resource_group>' \
>   --header 'Content-Type: application/json' \
>   --header 'Authorization: Bearer $TOKEN' \
>   --data '{
> 	  "name": "config-name",
> 	  "destinationName": "destination-name",
> 	  "dataRepositoryType": "<data repository type>",
> 	  "includePaths": [
> 	    "/path/one",
> 	    "/path/two"
> 	  ],
> 	  "labels": [
> 	    {
> 	      "key": "department",
> 	      "value": "finance"
> 	    }
> 	  ]
> 	}'
> 
> ```



## Results

Successful responses return code **202** and include a success message.

The response includes details of your metadata configuration resource, including the **metadata configuration ID**.

Document enumeration is performed asynchronously after the request is accepted.



## Next Steps

You can reference your metadata configuation as part of a pipeline by referencing the metadata configuration ID when you create your pipeline. For more information, see [Create a Pipeline using a Metadata Configuration](create-a-pipeline-using-a-metadata-configuration-454abf5.md).

