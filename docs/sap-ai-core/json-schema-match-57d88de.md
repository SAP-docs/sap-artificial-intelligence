<!-- loio57d88de0311c4b4493d762e83c0f14d2 -->

# JSON Schema Match

The `json_schema_match` metric validates whether the LLM's generated output conforms to a specified JSON schema. This is essential for applications that depend on structured data, requiring reliability and consistency for downstream tasks like API calls or database entries.



## Dataset formatting

This metric requires a column or mapped variable "json\_schema" in the dataset. This column must contain a valid JSON Schema object that defines the expected structure of the LLM's output.

A JSON Schema is a powerful tool for validating the structure of JSON data. For more information on how to construct a schema, see the official JSON Schema documentation [https://json-schema.org/](https://json-schema.org/).

The json\_schema column entries can be provided in the following ways:

-   Provide a schema for each row individually.
-   Provide a schema in a single row that will be automatically applied to all rows.

The following example datasets show identical schemas provided in different ways:

**Example 1: A single row is used to define all rows**


<table>
<tr>
<th valign="top">

Prompt

</th>
<th valign="top">

json\_schema

</th>
</tr>
<tr>
<td valign="top">

Extract info from: 'User is Jane Doe, age 29.'

</td>
<td valign="top">

\{"type": "object", "properties": \{"name": \{"type": "string"\}, "age": \{"type": "integer"\}\}, "required": \["name", "age"\]\}

</td>
</tr>
<tr>
<td valign="top">

Extract info from: 'User is John Smith, age 42.'

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Extract info from: 'User is Sam, age 35.'

</td>
<td valign="top">

 

</td>
</tr>
</table>

**Example 2: Each row is defined individually**


<table>
<tr>
<th valign="top">

Prompt

</th>
<th valign="top">

json\_schema

</th>
</tr>
<tr>
<td valign="top">

Extract info from: 'User is Jane Doe, age 29.'

</td>
<td valign="top">

\{"type": "object", "properties": \{"name": \{"type": "string"\}, "age": \{"type": "integer"\}\}, "required": \["name", "age"\]\}

</td>
</tr>
<tr>
<td valign="top">

Extract info from: 'User is John Smith, age 42.'

</td>
<td valign="top">

\{"type": "object", "properties": \{"name": \{"type": "string"\}, "age": \{"type": "integer"\}\}, "required": \["name", "age"\]\}

</td>
</tr>
<tr>
<td valign="top">

Extract info from: 'User is Sam, age 35.'

</td>
<td valign="top">

\{"type": "object", "properties": \{"name": \{"type": "string"\}, "age": \{"type": "integer"\}\}, "required": \["name", "age"\]\}

</td>
</tr>
</table>



## Example Evaluation

This example uses the following JSON schema to assess LLM outputs for a task that extracts user contact and priority information. The schema is defined in the `json_schema` column of your dataset.

```
{
  "type": "object",
  "properties": {
    "customer_name": { 
        "type": "string" 
    },
    "customer_email": {
        "type": "string",
        "format": "email"
    },
    "priority": {
        "type": "string",
        "enum": ["High", "Medium", "Low"]
    }
  },
  "required": ["customer_name", "customer_email", "priority"]
}

```



### Case 1: Valid Output \(Pass\)

This LLM output generates a well-structured JSON object that conforms perfectly to the schema:

> ### Output Code:  
> ```
> {
>   "customer_name": "Alex",
>   "customer_email": "alex@example.com",
>   "priority": "High"
> }
> 
> ```

Metric Score: 1 \(Pass\).

The reasoning for this result is as follows:

-   All required fields, for example `customer_name`, `customer_email` and `priority`, are present
-   Their data types are correct. For example, `priority` is a string, and `High` is a valid enum option.



### Case 2: Invalid Output \(Fail\)



This LLM output generates a JSON object that violates the schema in several ways:

> ### Output Code:  
> ```
> {
>   "name": "Alex",
>   "priority": 1
> }
> 
> ```

Metric Score: 0 \(Fail\).

The reasoning for this result is as follows:

-   Missing Required Field: the required field `customer_email` is missing.
-   Incorrect Field Name: the required field `customer_name` is missing; the LLM used name instead.
-   Incorrect Data Type: the value for priority is the integer `1`, but the schema requires a string.
-   Invalid Enum Value: the value 1 is not one of the allowed enum values: \[`High`, `Medium`, `Low`\].

