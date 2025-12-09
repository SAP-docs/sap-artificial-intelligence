<!-- loio884ae340eb4a409b9548aee135e98b3f -->

# Create Configurations

A configuration is a collection of parameters, artifact references \(such as datasets or models\), and environment settings that are used to instantiate and run an execution or deployment of an executable or template.

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_o2h_3bq_tcc"/>

## Procedure

Run the following code:

```
curl --request POST "$AI_API_URL/v2/lm/configurations" --header "Authorization: Bearer $TOKEN" --header "AI-Resource-Group: $RESOURCE_GROUP" --header "Content-Type: application/json" \
-d '{ 
    "name": "dummy-configuration", 
    "executableId": "'"$EXECUTABLE"'", 
    "scenarioId": "'"$SCENARIO"'", 
    "parameterBindings": [ 
      { 
        "key": "parameter_name_in_template", 
        "value": "some_value" 
      } 
    ], 
    "inputArtifactBindings": [ 
      { 
        "key": "input_artifact_name_in_template", 
        "artifactId": "a4d62a76-52aa-44cf-a789-743246d6d55b" 
      } 
    ] 
  }' 
```

> ### Output Code:  
> ```json
> {
>    "id":"f5bf305f-7c3f-4882-9f6b-8b95e3687b9b",
>    "message":"Configuration created"
> }
> ```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform



<a name="task_cxf_n13_tcc__steps_ysp_kbp_yxb"/>

## Procedure

1.  Send a POST request to the endpoint `{{apiurl}}/v2/lm/configurations`

2.  On the *Authorization* tab, set the type to *Bearer Token*.

3.  Set the token value to `{{token}}`.

4.  On the *Header* tab, add the following entries:


    <table>
    <tr>
    <th valign="top">

    KEY
    
    </th>
    <th valign="top">

    VALUE
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `AI-Resource-Group` 
    
    </td>
    <td valign="top">
    
    *<Name of your resourceGroup\>* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Content-Type` 
    
    </td>
    <td valign="top">
    
    `application/json` 
    
    </td>
    </tr>
    </table>
    
5.  On the *Body* tab, select the *raw* radio button and add the request body as given below:

    ```
    {
        "name": "configuration-name",
        "executableId": "<executable ID>",
        "scenarioId": "<scenario ID>",
        "parameterBindings": [
          {
            "key": "<parameter name>",
            "value": "<value>"
          }
        ],
        "inputArtifactBindings": [
          {
            "key": "<artifact name>",
            "artifactId": "<artifact ID>"
          }
        ]
      }
    
    ```

    > ### Output Code:  
    > ```
    > ...
    > "": [
    > {
    > "key": "churn-data",
    > "artifactId": "896e9230-9219-47fa-89c7-c47db7d45d6a"
    > }
    > ]
    > ```

6.  Send the request.


