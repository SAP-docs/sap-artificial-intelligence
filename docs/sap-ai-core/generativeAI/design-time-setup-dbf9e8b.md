<!-- loiodbf9e8b308bb4f089b58c78579e80736 -->

# Design-Time Setup

Design-time configuration prepares Tabular AI for runtime prediction. During this setup, you define how Tabular AI accesses data, interprets schema metadata, and selects relevant context rows for prediction.

Design-time setup is a one-time process that must be completed before you make predictions. It consists of the following steps:

1.  Connect Tabular AI to your storage back end.

    1.  Test the connection. No configuration is saved during the test.
    2.  Create the destination after the connection status changes to OK.

    For more information, see [Data Destination](data-destination-2d9b3ea.md).

2.  Onboard a specific file and its schema.

    1.  Submit the artifact creation request.
    2.  Poll until the status changes to `READY`.
    3.  Optionally, verify the data.

    For more information, see [Tabular Artifact](tabular-artifact-b490b79.md).

3.  Bind the tabular artifact to a context selection strategy. For more information, see [Scenario Configuration](scenario-configuration-12dd0b7.md).




## Common Conventions

Make sure that you've set the following headers:


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

The base URL of your SAP AI Core environment. You can set the URL as an environment variable.

</td>
</tr>
</table>



### Pagination Query Parameters

The following parameters are supported:


<table>
<tr>
<th valign="top">

**Parameter**

</th>
<th valign="top">

**Description**

</th>
<th valign="top">

**Type**

</th>
</tr>
<tr>
<td valign="top">

`$top`

</td>
<td valign="top">

Maximum number of results to return

</td>
<td valign="top">

Full result set

</td>
</tr>
<tr>
<td valign="top">

`$skip`

</td>
<td valign="top">

Number of results to skip

</td>
<td valign="top">

integer \(≥ 0\)

</td>
</tr>
<tr>
<td valign="top">

$count

</td>
<td valign="top">

When `true`, `count` reflects the total server-side record count

</td>
<td valign="top">

boolean

</td>
</tr>
</table>



### Naming Rules


<table>
<tr>
<th valign="top">

Resource

</th>
<th valign="top">

Pattern

</th>
<th valign="top">

Max Length

</th>
</tr>
<tr>
<td valign="top">

Data Destination

</td>
<td valign="top">

`^[a-z0-9]([-a-z0-9]*[a-z0-9])?$`

</td>
<td valign="top">

127 chars

</td>
</tr>
<tr>
<td valign="top">

Tabular Artifact

</td>
<td valign="top">

`^[a-z0-9]([-a-z0-9]*[a-z0-9])?$`

</td>
<td valign="top">

80 chars

</td>
</tr>
<tr>
<td valign="top">

Scenario Configuration

</td>
<td valign="top">

`^[a-z0-9]([-a-z0-9]*[a-z0-9])?$`

</td>
<td valign="top">

127 chars

</td>
</tr>
</table>

Entries must consist only of lowercase letters, digits, and hyphens. They must start and end with an alphanumeric character.



### Label Format


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Pattern

</th>
<th valign="top">

Max Length

</th>
</tr>
<tr>
<td valign="top">

`key`

</td>
<td valign="top">

Must start with `ext.ai.sap.com/`

</td>
<td valign="top">

63 chars

</td>
</tr>
<tr>
<td valign="top">

`value`

</td>
<td valign="top">

Alphanumeric character with hyphen \(-\), underscore \(\_\), period \(.\), comma \(,\), or slash \(/\)

</td>
<td valign="top">

63 chars

</td>
</tr>
</table>

When you PATCH labels, they're replaced in full, not merged with existing ones.



### Error Response Format

```
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "Data destination 'my-dd' not found",
    "requestId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "target": "/api/v1/tcr/dataDestinations/my-dd"
  }
}
```

-   **[Data Destination](data-destination-2d9b3ea.md)**  

-   **[Tabular Artifact](tabular-artifact-b490b79.md)**  

-   **[Scenario Configuration](scenario-configuration-12dd0b7.md)**  

-   **[Cleanup \(Optional\)](cleanup-optional-4884385.md)**  


