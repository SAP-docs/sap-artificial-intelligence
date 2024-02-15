<!-- loioab04f048da444d13bae08214c9d40e12 -->

# Store Metric Data

You can store metrics by submitting a PATCH request to the endpoint `/v2/lm/metrics`. To store tracking data, you must provide the parameter `AI-Resource-Group` header string.

The `executionId`, `metrics` `labels`, `tags`, and `customInfo` together form a MetricResource that is used as the request body for the PATCH API to persist tracking data.

The following limits apply to each of the attributes in the MetricResource:

-   `metrics` – maximum 1000

-   `labels` – maximum 20, with a maximum character limit of 256 for each label

-   `tags` – maximum 100, with a maximum character limit of 256 for each tag

-   `customInfo` – maximum 100, with a maximum size of 5 MB for the entire `customInfo` object


> ### Recommendation:  
> Do not use the tracking functions provided by SAP AI Core to track sensitive information. For more information, see [Security](security-a476d3c.md).



<a name="loioab04f048da444d13bae08214c9d40e12__section_ub1_rpf_ynb"/>

## `executionId`

A unique identifier for an execution.



<a name="loioab04f048da444d13bae08214c9d40e12__section_jrm_rpf_ynb"/>

## `metrics`

A metric is a key/value pair where the value is numeric. Metrics can have optional step, timestamp, and label fields. Metrics are captured as part of a training execution to evaluate a model's performance. Every metric \(and associated labels\), tag, and custom info must be associated with an execution. Once the metric, tag, and custom info are saved, they can be queried with an execution ID.

**Metrics Attributes**


<table>
<tr>
<th valign="top">

Attribute Name

</th>
<th valign="top">

Description

</th>
<th valign="top">

Type

</th>
<th valign="top">

Constraints

</th>
</tr>
<tr>
<td valign="top">

Name \(mandatory\)

</td>
<td valign="top">

Name of the metric

</td>
<td valign="top">

String

</td>
<td valign="top">

Pattern: \[\\w-\]\{1,64\}

Maxlength: 256

</td>
</tr>
<tr>
<td valign="top">

Value \(mandatory\)

</td>
<td valign="top">

Numeric value of the metric

</td>
<td valign="top">

Number

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Timestamp

</td>
<td valign="top">

Time when the metric was created or logged in RFC3339 format

</td>
<td valign="top">

String \($date-time\)

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Step

</td>
<td valign="top">

Step is an optional integer that represents any measurement of training progress \(number of training iterations, number of epochs, and so on\) for the metric

</td>
<td valign="top">

Integer

</td>
<td valign="top">

Minimum: 0

</td>
</tr>
<tr>
<td valign="top">

Labels

</td>
<td valign="top">

A list of name-value object pairs associated with some metric.

</td>
<td valign="top">

See [Table 2](store-metric-data-ab04f04.md#loioab04f048da444d13bae08214c9d40e12__table_tcs_wpf_ynb) 

</td>
<td valign="top">



</td>
</tr>
</table>



<a name="loioab04f048da444d13bae08214c9d40e12__section_oym_rpf_ynb"/>

## `labels`

A label is a classifying phrase or name applied to a metric. A set of labels can be used to provide each instance of a metric record with extra information.

**Label Attributes**


<table>
<tr>
<th valign="top">

Attribute Name

</th>
<th valign="top">

Description

</th>
<th valign="top">

Type

</th>
<th valign="top">

Constraints

</th>
</tr>
<tr>
<td valign="top">

Name \(mandatory\)

</td>
<td valign="top">

Name of the label

</td>
<td valign="top">

String

</td>
<td valign="top">

Minlength: 1

Maxlength: 256

</td>
</tr>
<tr>
<td valign="top">

Value \(mandatory\)

</td>
<td valign="top">

Value of the label

</td>
<td valign="top">

String

</td>
<td valign="top">

Minlength: 1

Maxlength: 256

</td>
</tr>
</table>

For a metric to be associated with a model, you must explicitly associate it with a model artifact:

> ### Sample Code:  
> ```
> "labels":[
>    {
>       "name":"group",
>       "value":"tree-82"
>    },
>    {
>       "name":"metrics.ai.sap.com/Artifact.name",
>       "value":"my_model_name"
>    }
> ]
> 									
> ```

When an execution produces only one output model artifact, all metrics captured in the execution are associated with that output artifact. If an execution produces more than one output model artifact, each metric captured must be explicitly associated with a model artifact \(as shown in the example above\).



<a name="loioab04f048da444d13bae08214c9d40e12__section_zgn_rpf_ynb"/>

## `tags`

A tag is a name/value pair that is used to support segregation at execution level. For example, you can assign tags to a group of selected test executions. A set of tags can be associated with a `MetricResource`, which in turn is linked to an execution.

**Tag Attributes**


<table>
<tr>
<th valign="top">

Attribute Name

</th>
<th valign="top">

Description

</th>
<th valign="top">

Type

</th>
<th valign="top">

Constraints

</th>
</tr>
<tr>
<td valign="top">

Name \(mandatory\)

</td>
<td valign="top">

Name of the tag

</td>
<td valign="top">

String

</td>
<td valign="top">

Minlength: 1

Maxlength: 256

</td>
</tr>
<tr>
<td valign="top">

Value \(mandatory\)

</td>
<td valign="top">

Value of the tag

</td>
<td valign="top">

String

</td>
<td valign="top">

Minlength: 1

Maxlength: 256

</td>
</tr>
</table>



<a name="loioab04f048da444d13bae08214c9d40e12__section_aqn_rpf_ynb"/>

## `customInfo`

Custom info key/value pairs that enable the capture of large amounts of metadata, typically associated with an execution. Custom info provides rendering or semantic information regarding a metric for a consuming application or complex metrics in JSON format.

A set of such custom info objects can be associated with a `MetricResource`.

**CustomInfo Attributes**


<table>
<tr>
<th valign="top">

Attribute Name

</th>
<th valign="top">

Description

</th>
<th valign="top">

Type

</th>
<th valign="top">

Constraints

</th>
</tr>
<tr>
<td valign="top">

Name \(mandatory\)

</td>
<td valign="top">

Name of the CustomInfo

</td>
<td valign="top">

String

</td>
<td valign="top">

Minlength: 1

Maxlength: 256

</td>
</tr>
<tr>
<td valign="top">

Value \(mandatory\)

</td>
<td valign="top">

Value of the CustomInfo

</td>
<td valign="top">

String

</td>
<td valign="top">

Minlength: 1

Maxlength: 256

</td>
</tr>
</table>



<a name="loioab04f048da444d13bae08214c9d40e12__section_tnh_1rf_ynb"/>

## Examples



### Example Request Body for PATCH API

```json
{
  "executionId": "aa97b177-9383-4934-8543-0f91a7a0283a",
  "metrics": [
    {
      "name": "Error Rate",
      "value": 0.98,
      "timestamp": "2020-11-12T12:18:01.539Z",
      "step": 2,
      "labels": [
        {
          "name": "group",
          "value": "tree-82"
        },
       {
         “name”: “metrics.ai.sap.com/Artifact.name”,
         “value”: “my_model_name”
       }
      ]
    }
  ],
  "tags": [
    {
      "name": "Artifact Group",
      "value": "RFC-1"
    }
  ],
  "customInfo": [
    {
      "name": "Confusion Matrix",
      "value": "[{'Predicted': 'False', 'Actual': 'False', 'value': 34}, {'Predicted': 'False', 'Actual': 'True', 'value': 124}, {'Predicted': 'True', 'Actual': 'False', 'value': 165}, {'Predicted': 'True', 'Actual': 'True', 'value': 36}]"
    }
  ]
}

```



### Responses of PATCH API


<table>
<tr>
<th valign="top">

Response Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

204

</td>
<td valign="top">

Metrics was successfully updated/created

</td>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

The specification of the resource was incorrect

</td>
</tr>
</table>

> ### Sample Code:  
> ```json
> {
>   "error": {
>     "code": "<error code>",
>     "message": "<error message>.",
>     "requestId": "9832bf934f3743v3948v3",
>     "target": "/metrics",
>     "details": [
>       {
>         "code": "<error code>",
>         "message": "<error message>"
>       }
>     ]
>   }
> }
> 
> ```


<table>
<tr>
<th valign="top">

Response Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

413

</td>
<td valign="top">

Request entity is larger than limits defined by server.

</td>
</tr>
</table>

> ### Sample Code:  
> ```json
> {
>   "error": {
>     "code": "02000005",
>     "message": "PayloadLimitException",
>     "requestId": "9832bf934f3743v3948v3",
>     "target": "/metrics",
>     "details": [
>       {
>         "code": "02000005",
>         "message": "PayloadLimitException"
>       }
>     ]
>   }
> }
> 
> ```

