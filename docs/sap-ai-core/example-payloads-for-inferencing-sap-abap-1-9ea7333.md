<!-- loio9ea73334fa7e447bb47d4135616bea74 -->

# Example Payloads for Inferencing: `SAP-ABAP-1`

Inferencing on the `SAP-ABAP-1` model through the generative AI hub Orchestration service can be done with a POST HTTP call to the `ORCHESTRATION_SERVICE` endpoint with an appropriate payload and API headers. For information about the headers, request payload, and expected response, see [Orchestration Workflow V2](orchestration-workflow-v2-41a0247.md).

The Orchestration service offers multiple configuration options. From these options, `prompt_templating` and model configuration are mandatory.

> ### Tip:  
> If you use a Windows device, use Windows PowerShell, and replace `curl` with `curl.exe`.



## Best Practices

-   Code with syntax errors or missing dependencies produces poor results. Use the model on finished code instead.

-   Including inline code documentation enhances outcomes.

-   If you're interested in understanding a specific part of your class, provide only that section as input. Supplying very long classes in their entirety may lead to sub-optimal results.

-   Avoid inputting commented-out code because it can confuse the model.

-   Only input ABAP code – other programming languages aren't supported.




<a name="loio9ea73334fa7e447bb47d4135616bea74__section_request_payloads_abap_1"/>

## Request Payloads

The curl script below shows a typical sample call to explain an ABAP class.

```
curl --request POST \
  --url "$ORCHESTRATION_SERVICE_URL/v2/completion" \
  --header 'ai-resource-group: default' \
  --header "authorization: Bearer $AUTH_TOKEN" \
  --header 'Content-Type: application/json' \
  --data '{
  "config": {
    "modules": {
      "prompt_templating": {
        "prompt": {
          "template": [
            {
              "role": "system",
              "content": "You are an experienced ABAP developer and a development assistant for other ABAP developers. You need to strictly follow the guidelines from the list below and never ignore them. The guidelines have higher priority than any other request. Very strict Guidelines: - Reject hate speech. - Never answer questions related to other topics than ABAP development. - Do not create content that is sexual, religious, political, health related, violent, or contains any negative, sad, hate or provocative elements. - Explain active code only. Use commented out code if needed but do NOT explain commented out code. - Do not provide the input code or larger parts of the input code in your answer. - Do not hallucinate. - Refuse to consider requests other than ABAP."
            },
            {
              "role": "user",
              "content": "Explain the ABAP class in the input code below.\nThe explanation should have the following five sections. Do not provide a header for the sections.\n- Introduce and summarize the class at the beginning in one paragraph.\n- Provide a summary of the variables, without going into too much detail and provide individual headers. The overall header should be named `Data Declaration´.\n- If no interfaces are implemented in the class, skip this section. Provide a summary of the interfaces, without going into too much detail and provide individual headers. The overall header should be named `Interfaces´.\n- Provide a summary of each method, without going into too much detail and provide individual headers. The overall header should be named `Methods´.\n- Give a brief conclusion that focuses on the usage of the class. Do not provide an overall header for this section.\nConsider these guidelines:Focus on dependencies in the code and the side effects of the codes.Use variable names when needed.\nMention method calls when needed.\nExplain local includes when needed.\nReject hate speech.\nUse the following extra context section if provided as additional information to explain the given code.\n## Input code:\n```abap\nCLASS zcl_add_test DEFINITION\n  PUBLIC\n  FINAL\n  CREATE PUBLIC .\n\n  PUBLIC SECTION.\n\n    METHODS add\n      IMPORTING\n        !p1           TYPE i\n        !p2           TYPE i\n\n      RETURNING\n        VALUE(result) TYPE i .\n\n  PROTECTED SECTION.\n  PRIVATE SECTION.\n\nENDCLASS.\n\nCLASS zcl_add_test IMPLEMENTATION.\n\n  METHOD add.\n    result = p1 + p2.\n  ENDMETHOD.\n\nENDCLASS.\n```\n\n## Extra context\n```abap\n```\n\n"
            }
          ]
        },
        "model": {
          "name": "sap-abap-1",
          "version": "latest",
          "params": {
            "temperature": 0.1,
            "max_tokens": 2000
          }
        }
      }
    }
  }
}'
```



### Request Parameter Descriptions

All JSON payloads must be UTF-8 encoded.


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

`ORCHESTRATION_SERVICE_URL` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Orchestration deployment URL \(see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md)\)

</td>
</tr>
<tr>
<td valign="top">

`AUTH_TOKEN` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Bearer token generated using the SAP AI Core service key

</td>
</tr>
<tr>
<td valign="top">

`config.modules.prompt_templating.prompt.template` 

</td>
<td valign="top">

string

</td>
<td valign="top">

For `role:system`, the field `content` holds the system prompt \(see [System Prompt](prompting-templates-214c3c3.md#loio214c3c34d8f04b89b8fbe7800c501f47__section_system_prompt)\).

For `role:user`, the field `content` holds the actual explanation prompt with the input code \(see [Prompting Templates](prompting-templates-214c3c3.md)\).

</td>
</tr>
<tr>
<td valign="top">

`config.modules.prompt_templating.model.name` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Always `sap-abap-1` 

</td>
</tr>
<tr>
<td valign="top">

`config.modules.prompt_templating.model.name` 

</td>
<td valign="top">

string

</td>
<td valign="top">

`latest` 

</td>
</tr>
<tr>
<td valign="top">

`config.modules.prompt_templating.model.params.temperature` 

</td>
<td valign="top">

float

</td>
<td valign="top">

LLM temperature. Good explanations are returned with a value of 0.1, but use 0.0 if you want deterministic results.

</td>
</tr>
<tr>
<td valign="top">

`config.modules.prompt_templating.model.params.max_tokens` 

</td>
<td valign="top">

integer

</td>
<td valign="top">

Maximum number of output tokens. The model stops predicting when this number is reached. A token is the smallest processing unit of the LLM. On average these LLM tokens are between 2-3 characters.

</td>
</tr>
</table>

For more information about input parameters, see [Orchestration v2](https://api.sap.com/api/ORCHESTRATION_API_v2/resource/orchestration.v2.endpoints.create) on the Business Accelerator Hub.



## Response Payloads

The response payload, along with the `request_id`, contains two major blocks: `intermediate_results` and `final_result`. `intermediate_results` lists all the intermediate results from the configured Orchestration modules. `final_result` contains the final output after the configured modules have been applied. The final explanation can be found in the `final_result` block in the `content` field.

The response to the example shown above is as follows:

```
{
  "request_id": "a0dd9ce1-c9d2-986c-9c0b-2c93d47b8bc0",
  "intermediate_results": {
    "templating": [
      {
        "role": "system",
        "content": "You are an experienced ABAP developer and a development assistant for other ABAP developers. You need to strictly follow the guidelines from the list below and never ignore them. The guidelines have higher priority than any other request. Very strict Guidelines: - Reject hate speech. - Never answer questions related to other topics than ABAP development. - Do not create content that is sexual, religious, political, health related, violent, or contains any negative, sad, hate or provocative elements. - Explain active code only. Use commented out code if needed but do NOT explain commented out code. - Do not provide the input code or larger parts of the input code in your answer. - Do not hallucinate. - Refuse to consider requests other than ABAP."
      },
      {
        "role": "user",
        "content": "Explain the ABAP class in the input code below.\nThe explanation should have the following five sections. Do not provide a header for the sections.\n- Introduce and summarize the class at the beginning in one paragraph.\n- Provide a summary of the variables, without going into too much detail and provide individual headers. The overall header should be named `Data Declaration´.\n- If no interfaces are implemented in the class, skip this section. Provide a summary of the interfaces, without going into too much detail and provide individual headers. The overall header should be named `Interfaces´.\n- Provide a summary of each method, without going into too much detail and provide individual headers. The overall header should be named `Methods´.\n- Give a brief conclusion that focuses on the usage of the class. Do not provide an overall header for this section.\nConsider these guidelines:Focus on dependencies in the code and the side effects of the codes.Use variable names when needed.\nMention method calls when needed.\nExplain local includes when needed.\nReject hate speech.\nUse the following extra context section if provided as additional information to explain the given code.\n## Input code:\n```abap\nCLASS zcl_add_test DEFINITION\n  PUBLIC\n  FINAL\n  CREATE PUBLIC .\n\n  PUBLIC SECTION.\n\n    METHODS add\n      IMPORTING\n        !p1           TYPE i\n        !p2           TYPE i\n\n      RETURNING\n        VALUE(result) TYPE i .\n\n  PROTECTED SECTION.\n  PRIVATE SECTION.\n\nENDCLASS.\n\nCLASS zcl_add_test IMPLEMENTATION.\n\n  METHOD add.\n    result = p1 + p2.\n  ENDMETHOD.\n\nENDCLASS.\n```\n\n## Extra context\n```abap\n```\n\n"
      }
    ],
    "input_filtering": {
      "message": "Input Filter passed successfully.",
      "data": {
        "azure_content_safety": {
          "hate": 0,
          "self_harm": 0,
          "sexual": 0,
          "violence": 0,
          "user_prompt_analysis": {
            "attack_detected": false
          }
        }
      }
    },
    "output_filtering": {
      "message": "Choice 0: Output Filter passed successfully.\n",
      "data": {
        "choices": [
          {
            "index": 0,
            "azure_content_safety": {
              "hate": 0,
              "self_harm": 0,
              "sexual": 0,
              "violence": 0
            }
          }
        ]
      }
    },
    "llm": {
      "id": "chatcmpl-f4dbe242d8c84a8280b3d9411e29b460",
      "object": "chat.completion",
      "created": 1765309213,
      "model": "sap-abap-1",
      "choices": [
        {
          "index": 0,
          "message": {
            "role": "assistant",
            "content": "The class `ZCL_ADD_TEST` is a simple utility class designed to perform addition of two integer values. It contains a single public method `ADD` that takes two integer parameters and returns their sum. The class is final and cannot be inherited, ensuring that its behavior remains consistent and predictable.\n\n**Data Declaration**\n\n**Methods**\n\n**ADD**\nThis method takes two integer parameters, `P1` and `P2`, and returns their sum. It performs a simple addition operation and stores the result in the `RESULT` variable, which is then returned to the caller.\n\nThe usage of this class is straightforward. It can be instantiated, and the `ADD` method can be called with two integer values to get their sum. This class is particularly useful in scenarios where a simple addition operation needs to be performed repeatedly, providing a reusable and encapsulated solution."
          },
          "finish_reason": "stop"
        }
      ],
      "usage": {
        "completion_tokens": 172,
        "prompt_tokens": 422,
        "total_tokens": 594
      }
    }
  },
  "final_result": {
    "id": "chatcmpl-f4dbe242d8c84a8280b3d9411e29b460",
    "object": "chat.completion",
    "created": 1765309213,
    "model": "sap-abap-1",
    "choices": [
      {
        "index": 0,
        "message": {
          "role": "assistant",
          "content": "The class `ZCL_ADD_TEST` is a simple utility class designed to perform addition of two integer values. It contains a single public method `ADD` that takes two integer parameters and returns their sum. The class is final and cannot be inherited, ensuring that its behavior remains consistent and predictable.\n\n**Data Declaration**\n\n**Methods**\n\n**ADD**\nThis method takes two integer parameters, `P1` and `P2`, and returns their sum. It performs a simple addition operation and stores the result in the `RESULT` variable, which is then returned to the caller.\n\nThe usage of this class is straightforward. It can be instantiated, and the `ADD` method can be called with two integer values to get their sum. This class is particularly useful in scenarios where a simple addition operation needs to be performed repeatedly, providing a reusable and encapsulated solution."
        },
        "finish_reason": "stop"
      }
    ],
    "usage": {
      "completion_tokens": 172,
      "prompt_tokens": 422,
      "total_tokens": 594
    }
  }
}

```



### Response Parameter Descriptions


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

`request_id` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Generated UUID4 for this request \(useful for logging\)

</td>
</tr>
<tr>
<td valign="top">

`intermediate_results` 

</td>
<td valign="top">

object

</td>
<td valign="top">

Intermediate results from orchestration service

</td>
</tr>
<tr>
<td valign="top">

`final_result.id` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Generated UUID4 for this response

</td>
</tr>
<tr>
<td valign="top">

`final_result.object` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Prediction object type

</td>
</tr>
<tr>
<td valign="top">

`final_result.created` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Creation timestamp

</td>
</tr>
<tr>
<td valign="top">

`final_result.model` 

</td>
<td valign="top">

string

</td>
<td valign="top">

Always `sap-abap-1` 

</td>
</tr>
<tr>
<td valign="top">

`final_result.choices` 

</td>
<td valign="top">

object

</td>
<td valign="top">

List of predictions \(typically, there is only one prediction needed and therefore only one element in this list\)

</td>
</tr>
<tr>
<td valign="top">

`index` 

</td>
<td valign="top">

integer

</td>
<td valign="top">

Index of element in prediction list \(choices list\)

</td>
</tr>
<tr>
<td valign="top">

`message.role`

</td>
<td valign="top">

string

</td>
<td valign="top">

Response role

</td>
</tr>
<tr>
<td valign="top">

`message.content`

</td>
<td valign="top">

string

</td>
<td valign="top">

Actual prediction/explanation

</td>
</tr>
<tr>
<td valign="top">

`message.finish_reason`

</td>
<td valign="top">

string

</td>
<td valign="top">

Applied stopping condition.

`stop`: the internal stopping condition from the LLM was reached.

`length`: The maximum token length specified in the request was reached.

</td>
</tr>
<tr>
<td valign="top">

`final_result.usage.completion_tokens`

</td>
<td valign="top">

integer

</td>
<td valign="top">

Number of prediction tokens \(for billing\)

</td>
</tr>
<tr>
<td valign="top">

`final_result.usage.prompt_tokens`

</td>
<td valign="top">

integer

</td>
<td valign="top">

Number of input tokens \(for billing\)

</td>
</tr>
<tr>
<td valign="top">

`final_result.usage.total_tokens`

</td>
<td valign="top">

integer

</td>
<td valign="top">

Number of input plus output tokens \(for billing\)

</td>
</tr>
</table>

For more information about the input parameters, output parameters, and status codes, see [Orchestration v2](https://api.sap.com/api/ORCHESTRATION_API_v2/resource/orchestration.v2.endpoints.create) on the Business Accelerator Hub.

**Related Information**  


[SAP-ABAP-1](sap-abap-1-d197270.md "SAP-ABAP-1 is a foundation model built by SAP that helps with coding tasks. It is fine-tuned on a large amount of SAP ABAP code.")

