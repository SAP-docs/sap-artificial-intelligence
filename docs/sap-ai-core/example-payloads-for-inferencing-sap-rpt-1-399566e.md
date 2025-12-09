<!-- loio399566eec2404915ac69077cfa23f7b8 -->

# Example Payloads for Inferencing - `sap-rpt-1`

> ### Tip:  
> If you use a Windows device, use Windows PowerShell, and replace `curl` with `curl.exe`.

Ensure that you have set the following headers:


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

Bearer $AUTH\_TOKEN

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

$DEPLOYMENT\_URL

</td>
<td valign="top">

The deployment URL for your generative AI model. For more information, see [Create a Deployment for a Generative AI Model](create-a-deployment-for-a-generative-ai-model-b32e7a8.md).

Alternatively, you can replace the `$DEPLOYMENT_URL` placeholder in the curl command with your deployment URL.

</td>
</tr>
</table>

The `executableId` is `aicore-sap`.



## Best Practices

To achieve the best possible outputs, ensure that your requests comply with the following best practices:

-   Use clean data with no or minimum missing values.

-   Use descriptive column names \(under 100 characters\).

-   Limit descriptions in text columns to 500 characters.

-   Keep data types consistent within each column.

-   Consider removing unnecessary columns from the prediction task.


> ### Note:  
> The accuracy and fairness of the model’s predictions depend on the quality and balance of the data provided. Any bias present in the input data can result in biased or skewed outputs. SAP isn't responsible or liable for any bias, inaccuracy, or unintended outcome arising from user-provided data or its characteristics.



## Request Payloads

All JSON payloads must be UTF-8 encoded. To send gzip-compressed JSON payloads, set the header `Context-Encoding: gzip`.

`sap-rpt-1` accepts tabular data requests in the following formats:

-   Data as JSON organized by rows

-   Data as JSON organized by columns

-   Data in Apache Parquet file format


You can make requests using the following methods:



### Request with Data by Rows

```
curl --request POST \
  --url '$DEPLOYMENT_URL/predict' \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'content-type: application/json' \
  --data '{
    "prediction_config": {
        "target_columns": [
            {
                "name": "COSTCENTER",
                "prediction_placeholder": "[PREDICT]",
                "task_type": "classification"
            }
        ]
    },
    "index_column": "ID",
    "rows": [
        {
            "PRODUCT": "Couch",
            "PRICE": 999.99,
            "ORDERDATE": "28-11-2025",
            "ID": "35",
            "COSTCENTER": "[PREDICT]"
        },
        {
            "PRODUCT": "Office Chair",
            "PRICE": 150.8,
            "ORDERDATE": "02-11-2025",
            "ID": "44",
            "COSTCENTER": "Office Furniture"
        },
        {
            "PRODUCT": "Server Rack",
            "PRICE": 2200.00,
            "ORDERDATE": "01-11-2025",
            "ID": "104",
            "COSTCENTER": "Data Infrastructure"
        }
    ],
    "data_schema": {
        "PRODUCT": {
            "dtype": "string"
        },
        "PRICE": {
            "dtype": "numeric"
        },
        "ORDERDATE": {
            "dtype": "date"
        },
        "ID": {
            "dtype": "string"
        },
        "COSTCENTER": {
            "dtype": "string"
        }
    }
}'
```



### Request with Data by Columns

```
curl --request POST \
  --url '$DEPLOYMENT_URL/predict' \
  --header 'AI-Resource-Group: default' \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header 'Content-Type: application/json' \
  --data '{
  "prediction_config": {
    "target_columns": [
      {
        "name": "COSTCENTER",
        "prediction_placeholder": "[PREDICT]",
        "task_type": "classification"
      }
    ]
  },
  "index_column": "ID",
  "columns": {
      "PRODUCT": ["Couch", "Office Chair", "Server Rack"],
      "PRICE": [999.99, 150.8, 2200.00],
      "ORDERDATE": ["28-11-2025", "02-11-2025", "01-11-2025"],
      "ID": ["35", "44", "104"],
      "COSTCENTER": ["[PREDICT]", "Office Furniture", "Data Infrastructure"]
  },
  "data_schema": {
      "PRODUCT": {
          "dtype": "string"
      },
      "PRICE": {
          "dtype": "numeric"
      },
      "ORDERDATE": {
          "dtype": "date"
      },
      "ID": {
          "dtype": "string"
      },
      "COSTCENTER": {
          "dtype": "string"
      }
  }
}'
```



### Request with Parquet File

Parquet files can be uploaded using multipart form-data.

The request must include the following form fields:

-   `file`: The parquet file to be uploaded \(`Content-Type: application/octet-stream`\)

-   `prediction_config`: A JSON string containing the prediction configuration

-   `index_column`: The name of the column used to identify the row

-   `parse_data_types`: A boolean that specifies whether to parse data types automatically \(default: `true`\)


The values for the `index_column` and `parse_data_types` fields are optional but recommended. If you don't specify values for these fields, the system uses default values.

The request must use `Content-Type: multipart/form-data` with an appropriate boundary string. The parquet file is read and processed similarly to row-wise and column-wise JSON inputs.

```
POST $DEPLOYMENT_URL/predict_parquet
  --header "Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW" \
  --header "Authorization: Bearer $AUTH_TOKEN" \
  --header "ai-resource-group: default"

------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="file"; filename="test_data.parquet"
Content-Type: application/octet-stream

< ./test_data.parquet
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="prediction_config"

{"target_columns": [{"name": "salary","prediction_placeholder": "[PREDICT]"}]}

------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="index_column"

name
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="parse_data_types"

true
------WebKitFormBoundary7MA4YWxkTrZu0gW--
```



## Parameters



### Parameter Description for `/predict` \(JSON input\)


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`prediction_config` 

</td>
<td valign="top">

object

</td>
<td valign="top">

The configuration object specifying which columns to predict

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.target_columns` 

</td>
<td valign="top">

array

</td>
<td valign="top">

An array of target-column configurations for prediction

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.target_columns[].name` 

</td>
<td valign="top">

string

</td>
<td valign="top">

The name of the column to predict

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.target_columns[].prediction_placeholder` 

</td>
<td valign="top">

string

</td>
<td valign="top">

The value used as placeholder in rows where prediction is needed

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.target_columns[].task_type` 

</td>
<td valign="top">

string

</td>
<td valign="top">

\(Optional\)

The type of prediction task

Possible values: `classification` or `regression`

If omitted, the model tries to automatically determine the task type that the user intends.

</td>
</tr>
<tr>
<td valign="top">

`index_column` 

</td>
<td valign="top">

string

</td>
<td valign="top">

\(Optional\)

The name of the column used to identify the row

This column isn't used as an input feature for the model, and is returned in the response objects.

</td>
</tr>
<tr>
<td valign="top">

`rows` 

</td>
<td valign="top">

array

</td>
<td valign="top">

An array of objects representing table rows \(both context and query rows\)

The keys of the objects are column names, for example `[{"product": "hammer", "price": 42.99, "creation_date": "2025-01-30"}, ...]`

</td>
</tr>
<tr>
<td valign="top">

`columns` 

</td>
<td valign="top">

object

</td>
<td valign="top">

An object mapping from column name to array of column values. You can pass rows only or columns only, for example `{"product": ["hammer", "nail", ...], "price": [42.99, 1.98, ...], "creation_date": ["2025-01-30", "2025-01-31", ...]}`

</td>
</tr>
<tr>
<td valign="top">

`data_schema` 

</td>
<td valign="top">

object

</td>
<td valign="top">

\(Optional\)

A schema definition for data types of all columns, for example `{"columnA": {"dtype": "text"}, "columnB": {"dtype": "numeric"}, ...}`

</td>
</tr>
<tr>
<td valign="top">

`data_schema.*.dtype` 

</td>
<td valign="top">

string

</td>
<td valign="top">

A data type specification. Possible values: `string`, `numeric`, or `date`

</td>
</tr>
<tr>
<td valign="top">

`parse_data_types` 

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

Relevant when `data_schema` isn't passed

Whether or not to parse data types, such as interpreting strings as numbers or dates

Default value: `true`

</td>
</tr>
</table>

The `data_schema parameter` and `task_type` parameters are optional, but are recommended to obtain the best prediction results.

If `data_schema` is omitted, data types are inferred automatically.

If `task_type` is omitted, the model attempts to determine whether `classification` or `regression` is the intended task type.



### Parameter description for `/predict_parquet` \(Parquet file input as multipart/form-data\)


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`prediction_config` 

</td>
<td valign="top">

object

</td>
<td valign="top">

The configuration object specifying which columns to predict

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.target_columns` 

</td>
<td valign="top">

array

</td>
<td valign="top">

The array of target-column configurations for prediction

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.target_columns[].name` 

</td>
<td valign="top">

string

</td>
<td valign="top">

The name of the column to predict

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.target_columns[].prediction_placeholder` 

</td>
<td valign="top">

string

</td>
<td valign="top">

The value used as placeholder in rows where prediction is needed

</td>
</tr>
<tr>
<td valign="top">

`prediction_config.target_columns[].task_type` 

</td>
<td valign="top">

string

</td>
<td valign="top">

\(Optional\)

The type of prediction task

Possible values: `classification` or `regression`

If omitted, the model tries to automatically determine the task type that the user intends.

</td>
</tr>
<tr>
<td valign="top">

`index_column` 

</td>
<td valign="top">

string

</td>
<td valign="top">

\(Optional\)

The name of the column used to identify the row

This column isn't used as an input feature for the model, and is returned in the response objects.

</td>
</tr>
<tr>
<td valign="top">

`file` 

</td>
<td valign="top">

application/octet-stream

</td>
<td valign="top">

A parquet file

</td>
</tr>
</table>



## Response Payload

The objects in `predictions` are sequence aligned with the order of the query rows in the request JSON.

If the `index_column` parameter has been passed, the contents of this column is also included in the response.

To align the response to the source data, you can sequence-align the arrays, or compare the contents of the index column where included.


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`id`

</td>
<td valign="top">

string

</td>
<td valign="top">

The generated UUID4 for this request \(useful for logging\)

</td>
</tr>
<tr>
<td valign="top">

`status`

</td>
<td valign="top">

object

</td>
<td valign="top">

The status message object indicating success of the prediction request

</td>
</tr>
<tr>
<td valign="top">

`status.code`

</td>
<td valign="top">

integer

</td>
<td valign="top">

The numeric status code.

For more information, see [Table 1](example-payloads-for-inferencing-sap-rpt-1-399566e.md#loio399566eec2404915ac69077cfa23f7b8__table_dym_vpq_4hc).

</td>
</tr>
<tr>
<td valign="top">

`status.message`

</td>
<td valign="top">

string

</td>
<td valign="top">

The status message text

</td>
</tr>
<tr>
<td valign="top">

`predictions[].*[].prediction`

</td>
<td valign="top">

string or float

</td>
<td valign="top">

The predicted value for this column

</td>
</tr>
<tr>
<td valign="top">

`predictions[].*[].confidence`

</td>
<td valign="top">

float or null

</td>
<td valign="top">

\(For `classification` tasks only\)

The confidence score for this prediction

</td>
</tr>
<tr>
<td valign="top">

`metadata.num_rows`

</td>
<td valign="top">

integer

</td>
<td valign="top">

The total number of input rows

</td>
</tr>
<tr>
<td valign="top">

`metadata.num_columns`

</td>
<td valign="top">

integer

</td>
<td valign="top">

The total number of input columns

</td>
</tr>
<tr>
<td valign="top">

`metadata.num_predictions`

</td>
<td valign="top">

integer

</td>
<td valign="top">

The number of table cells containing the specified placeholder values summed over all target columns

</td>
</tr>
<tr>
<td valign="top">

metadata.num\_query\_rows

</td>
<td valign="top">

integer

</td>
<td valign="top">

The number of query rows for which a prediction was made

</td>
</tr>
</table>

> ### Note:  
> Error responses can contain an additional array called `detail`, following pydantic format. For more information, see [Table 1](example-payloads-for-inferencing-sap-rpt-1-399566e.md#loio399566eec2404915ac69077cfa23f7b8__table_dym_vpq_4hc).



## Status Codes and Messages

A status code is returned to indicate success, a warning, or an error. Status codes can be any of the following:

**Status Codes and Messages**


<table>
<tr>
<th valign="top">

Code

</th>
<th valign="top">

Message

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

OK

</td>
<td valign="top">

Everything worked as expected.

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

Warning: At least one target column had invalid values in some context rows \(expected float-like values for regression\). These rows were dropped. Double-check your data; prediction accuracy may be impacted.

</td>
<td valign="top">

Sub optimal data/accuracy warning still returns predictions.

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

Invalid input

</td>
<td valign="top">

The input was invalid:

It could contain, for example.

-   Malformed JSON
-   Missing properties
-   Incorrectly typed properties
-   Maximum restrictions exceeded



</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

Internal server error

</td>
<td valign="top">

An unexpected error occurred.

</td>
</tr>
</table>



### Successful Prediction \(200\)

If the parameter `index_column` is specified in the request JSON, the following apply:

-   Each prediction object in the array contains an index column. In the following examples, the index column is called `ID`.

-   The column referenced as the `index_column` isn't input to the model and serves as index information in the response JSON.


> ### Output Code:  
> ```
> {
>     "id": "c334f854-0d70-4c79-bd73-9ac581fd8cda",
>     "status": {
>         "code": 0,
>         "message": "ok"
>     },
>     "predictions": [
>         {
>             "COSTCENTER": [
>                 {
>                     "prediction": "Office Furniture",
>                     "confidence": 0.96
>                 }
>             ],
>             "ID": "35"
>         }
>     ],
>     "metadata": {
>         "num_columns": 5,
>         "num_rows": 2,
>         "num_predictions": 1,
>         "num_query_rows": 1
>     }
> }
> ```



### Successful Prediction \(200\) with Warning

This example shows an output where the request to perform a regression contains either empty strings or null values in the regression target column.

```
{
    "id": "bf9018c4-f903-4035-a433-7058cb289447",
    "status": {
        "code": 1,
        "message": "Warning: At least one target column had invalid values in some context rows (expected float-like values for regression). These rows where dropped. Double-check your data, prediction accuracy may be impacted."
    },
    "predictions": [
        {
            "salary": [
                {
                    "prediction": 52451.3984375,
                    "confidence": null
                }
            ]
        }
    ],
    "metadata": {
        "num_columns": 4,
        "num_rows": 2,
        "num_predictions": 1,
        "num_query_rows": 1
    }
}
```



### Bad Request or Unprocessable Content \(400 or 422\)

```
{
    "status": {
        "code": 2,
        "message": "Invalid input"
    },
    "detail": [
        {
            "loc": [],
            "msg": "Too many query rows provided. Maximum is 128.",
            "type": "value_error"
        }
    ]
}
```

```
{
    "status": {
        "code": 2,
        "message": "Invalid input"
    },
    "detail": [
        {
            "loc": [
                "prediction_config",
                "target_columns",
                0,
                "prediction_placeholder"
            ],
            "msg": "Field required",
            "type": "missing"
        }
    ]
}
```



### Internal Server Error \(500\)

> ### Output Code:  
> ```
> {
>     "status": 3,
>     "message": "Internal server error"
> }
> ```

