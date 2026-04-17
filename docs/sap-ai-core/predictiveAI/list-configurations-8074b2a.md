<!-- loio8074b2a206cb41a2a68ba149a2150ea1 -->

# List Configurations

<a name="task_i3h_n13_tcc"/>

<!-- task\_i3h\_n13\_tcc -->

## Using Curl



<a name="task_i3h_n13_tcc__steps_dh5_ybq_tcc"/>

## Procedure

Run the following code:

```
curl --request GET "$AI_API_URL/v2/lm/configurations" --header "Authorization: Bearer $TOKEN" --header "AI-Resource-Group: $RESOURCE_GROUP"
```

> ### Output Code:  
> ```json
> {
>    "count":2,
>    "resources":[
>       {
>          "createdAt":"2021-02-04T11:50:45Z",
>          "executableId":"pytf-training",
>          "id":"1e6c2a5f-eabe-49a2-88e7-887145a2ef88",
>          "inputArtifactBindings":[
>             {
>                "artifactId":"521f7f17-876e-4369-9162-09748b56d27a",
>                "key":"churn-data"
>             },
>             {
>                "artifactId":"521f7f17-876e-4369-9162-09748b56d27a",
>                "key":"textclass-data"
>             }
>          ],
>          "name":"pytf-demo-config1",
>          "parameterBindings":[
>             {
>                "key":"train-epoch",
>                "value":"100"
>             }
>          ],
>          "scenarioId":"84fe6957-1145-4183-b682-8f11ca56d060"
>       },
>       {
>          "createdAt":"2021-02-04T11:59:22Z",
>          "executableId":"pytf-training",
>          "id":"42147d0d-5e3a-424d-a3a1-545b842379c5",
>          "inputArtifactBindings":[
>             {
>                "artifactId":"521f7f17-876e-4369-9162-09748b56d27a",
>                "key":"churn-data"
>             },
>             {
>                "artifactId":"521f7f17-876e-4369-9162-09748b56d27a",
>                "key":"textclass-data"
>             }
>          ],
>          "name":"pytf-demo-config2",
>          "parameterBindings":[
>             {
>                "key":"train-epoch",
>                "value":"1"
>             }
>          ],
>          "scenarioId":"84fe6957-1145-4183-b682-8f11ca56d060"
>       }
>    ]
> }
> ```

<a name="task_cxf_n13_tcc"/>

<!-- task\_cxf\_n13\_tcc -->

## Using a Third-Party API Platform

<a name="loioe9b4adcdd09a42719e14f04e550ebbc9"/>

<!-- loioe9b4adcdd09a42719e14f04e550ebbc9 -->

### List Configurations



<a name="loioe9b4adcdd09a42719e14f04e550ebbc9__steps_ufj_zbq_tcc"/>

## Procedure

1.  Send a GET request to the endpoint `{{apiurl}}/v2/lm/configurations`

2.  On the *Authorization* tab, set the type to *Bearer Token*.

3.  Set the token value to `{{token}}`.

4.  On the *Header* tab, add the following entry:


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
    </table>
    
5.  Send the request.

    ```
    {
    	"count": 45,
    	"resources": [
    	{
    		"createdAt": "2021-11-22Z06:51:03Z",
    		"executableId": "text-clf-train-tutorial-metrics",
    ...
    ```


