<!-- loio592c570f22734ec5ba7881a0aeb49c50 -->

# Enhancing Model Consumption with Data Masking



<a name="loio592c570f22734ec5ba7881a0aeb49c50__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio592c570f22734ec5ba7881a0aeb49c50__section_yqp_1rj_12c"/>

## Process

In the following example, we use the data masking module to anonymize people, organizations, and contact information in the input. The allow list contains the entries “Harvard University” and “Boston”, and so these are not masked. Here, input is masked before the model is called. The data in the model's output cannot be unmasked.

> ### Sample Code:  
> ```
> 
> curl --request POST $ORCH_DEPLOYMENT_URL/completion \
>     --header 'content-type: application/json' \
>     --header "Authorization: Bearer $TOKEN" \
>     --header "AI-Resource-Group: $RESOURCE_GROUP" \
>     --data-raw '{
>   "orchestration_config": {
>     "module_configurations": {
>       "templating_module_config": {
>         "template": [
>           {
>             "role": "user",
>             "content": "Summarize the following CV in 10 sentences: {{?orgCV}}"
>           }
>         ]
>       },
>       "llm_module_config": {
>         "model_name": "gpt-4",
>         "model_params": {
>           "max_tokens": 300,
>           "temperature": 0.1,
>           "frequency_penalty": 0,
>           "presence_penalty": 0
>         }
>       },
>       "masking_module_config": {
>         "masking_providers": [
>           {
>             "type": "sap_data_privacy_integration",
>             "method": "anonymization",
>             "entities": [
>               {"type": "profile-email"},
>               {"type": "profile-person"},
>               {"type": "profile-phone"},             
>               {"type": "profile-org"},
>               {"type": "profile-location"}
>               ],
>               "allowlist": ["Harvard University", "Boston"] // "Harvard University" and "Boston" will be preserved and not masked
>           }
>         ]
>       }
>     }
>   },
>   "input_params": {
>     "orgCV": "Patrick Morgan \n +49 (970) 333-3833 \n patric.morgan@hotmail.com \n\n Highlights \n - Strategic and financial planning expert \n - Accurate forecasting \n - Process implementation \n - Staff leadership and development \n - Business performance improvement \n - Proficient in SAP,  Excel VBA\n\n Education \n Master of Science: Finance - 2014 \n Harvard University, Boston \n\n Bachelor of Science: Finance - 2011 \n Harvard University, Boston \n\n\n Certifications \n Certified Management Accountant \n\n\n Summary \n Skilled Financial Manager adept at increasing work process efficiency and profitability through functional and technical analysis. Successful at advising large corporations, small businesses, and individual clients. Areas of expertise include asset allocation, investment strategy, and risk management. \n\n\n Experience \n Finance Manager - 09/2016 to 05/2018 \n M&K Group, York \n - Manage the modelling, planning, and execution of all financial processes. \n - Carry short and long-term custom comprehensive financial strategies to reach company goals. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Research market trends and surveys and use information to stimulate business. \n\n Finance Manager - 09/2013 to 05/2016 \n Ago Group, Chicago \n - Drafted executive analysis reports highlighting business issues, potential risks, and profit opportunities. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Analysed market trends and surveys and used information to revenue growth."
>   }
> }'
> ```

As shown in the response, the data masking module masks the configured entities before sending them to the model. The model then operates on this masked data and can still provide a summary.

> ### Output Code:  
> ```
> {
>   "request_id": "0b32ef8d-5f92-43de-ae2b-ae23cecba662",
>   "module_results": {
>     "templating": [
>       {
>         "role": "user",
>         "content": "Summarize the following CV in 10 sentences: Patrick Morgan \n +49 (970) 333-3833 \n patric.morgan@hotmail.com \n\n Highlights \n - Strategic and financial planning expert \n - Accurate forecasting \n - Process implementation \n - Staff leadership and development \n - Business performance improvement \n - Proficient in SAP,  Excel VBA\n\n Education \n Master of Science: Finance - 2014 \n Harvard University, Boston \n\n Bachelor of Science: Finance - 2011 \n Harvard University, Boston \n\n\n Certifications \n Certified Management Accountant \n\n\n Summary \n Skilled Financial Manager adept at increasing work process efficiency and profitability through functional and technical analysis. Successful at advising large corporations, small businesses, and individual clients. Areas of expertise include asset allocation, investment strategy, and risk management. \n\n\n Experience \n Finance Manager - 09/2016 to 05/2018 \n M&K Group, York \n - Manage the modelling, planning, and execution of all financial processes. \n - Carry short and long-term custom comprehensive financial strategies to reach company goals. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Research market trends and surveys and use information to stimulate business. \n\n Finance Manager - 09/2013 to 05/2016 \n Ago Group, Chicago \n - Drafted executive analysis reports highlighting business issues, potential risks, and profit opportunities. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Analysed market trends and surveys and used information to revenue growth."
>       }
>     ],
>     "input_masking": {
>       "message": "Input to LLM is masked successfully.",
>       "data": {
>         "masked_template": [
>           {
>             "role": "user",
>             "content": "Summarize the following CV in 10 sentences: MASKED_PERSON \n MASKED_PHONE_NUMBER \n MASKED_EMAIL \n\n Highlights \n - Strategic and financial planning expert \n - Accurate forecasting \n - Process implementation \n - Staff leadership and development \n - Business performance improvement \n - Proficient in SAP, Excel VBA\n\n Education \n Master of Science: Finance - 2014 \n Harvard University, Boston \n\n Bachelor of Science: Finance - 2011 \n Harvard University, Boston \n\n\n Certifications \n Certified Management Accountant \n\n\n Summary \n Skilled Financial Manager adept at increasing work process efficiency and profitability through functional and technical analysis. Successful at advising large corporations, small businesses, and individual clients. Areas of expertise include asset allocation, investment strategy, and risk management. \n\n\n Experience \n Finance Manager - 09/2016 to 05/2018 \n MASKED_ORG, MASKED_LOCATION \n - Manage the modelling, planning, and execution of all financial processes. \n - Carry short and long-term custom comprehensive financial strategies to reach company goals. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Research market trends and surveys and use information to stimulate business. \n\n Finance Manager - 09/2013 to 05/2016 \n MASKED_ORG, MASKED_LOCATION \n - Drafted executive analysis reports highlighting business issues, potential risks, and profit opportunities. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Analysed market trends and surveys and used information to revenue growth."          
>           }
>         ]
>       }
>     },
>     "llm": {
>       "id": "chatcmpl-A5vfibe3l7gpZLPKQnym4NLmknErY",
>       "object": "chat.completion",
>       "created": 1725976694,
>       "model": "gpt-4",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "The CV belongs to a skilled Financial Manager with expertise in strategic and financial planning, accurate forecasting, process implementation, staff leadership and development, and business performance improvement. They are proficient in SAP and Excel VBA. They hold a Master of Science in Finance from an undisclosed institution and location, and a Bachelor of Science in Finance from another undisclosed institution and location. They are also a Certified Management Accountant. Their experience includes managing financial processes, implementing financial strategies, recommending cost-saving measures, and conducting deal analysis and market research. They have worked as a Finance Manager for two different organizations from 2013 to 2018."
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 124,
>         "prompt_tokens": 354,
>         "total_tokens": 478
>       }
>     }
>   },
>   "orchestration_result": {
>     "id": "chatcmpl-A5vfibe3l7gpZLPKQnym4NLmknErY",
>     "object": "chat.completion",
>     "created": 1725976694,
>     "model": "gpt-4",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "The CV belongs to a skilled Financial Manager with expertise in strategic and financial planning, accurate forecasting, process implementation, staff leadership and development, and business performance improvement. They are proficient in SAP and Excel VBA. They hold a Master of Science in Finance from an undisclosed institution and location, and a Bachelor of Science in Finance from another undisclosed institution and location. They are also a Certified Management Accountant. Their experience includes managing financial processes, implementing financial strategies, recommending cost-saving measures, and conducting deal analysis and market research. They have worked as a Finance Manager for two different organizations from 2013 to 2018."
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 124,
>       "prompt_tokens": 354,
>       "total_tokens": 478
>     }
>   }
> }
> ```

When you use `"method": "pseudonymization"` instead of `"method": "anonymization"` in the masking module configuration, the data is pseudonymized before it's sent to the model. Additionally, the system checks the model's response for any data that can be unmasked before sending out the final response.

> ### Output Code:  
> ```
> {
>   "request_id": "f5d14279-9cbe-4f35-815d-ea2df5f6d9d4",
>   "module_results": {
>     "templating": [
>       {
>         "role": "user",
>         "content": "Summarize the following CV in 10 sentences: Patrick Morgan \n +49 (970) 333-3833 \n patric.morgan@hotmail.com \n\n Highlights \n - Strategic and financial planning expert \n - Accurate forecasting \n - Process implementation \n - Staff leadership and development \n - Business performance improvement \n - Proficient in SAP,  Excel VBA\n\n Education \n Master of Science: Finance - 2014 \n Harvard University, Boston \n\n Bachelor of Science: Finance - 2011 \n Harvard University, Boston \n\n\n Certifications \n Certified Management Accountant \n\n\n Summary \n Skilled Financial Manager adept at increasing work process efficiency and profitability through functional and technical analysis. Successful at advising large corporations, small businesses, and individual clients. Areas of expertise include asset allocation, investment strategy, and risk management. \n\n\n Experience \n Finance Manager - 09/2016 to 05/2018 \n M&K Group, York \n - Manage the modelling, planning, and execution of all financial processes. \n - Carry short and long-term custom comprehensive financial strategies to reach company goals. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Research market trends and surveys and use information to stimulate business. \n\n Finance Manager - 09/2013 to 05/2016 \n Ago Group, Chicago \n - Drafted executive analysis reports highlighting business issues, potential risks, and profit opportunities. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Analysed market trends and surveys and used information to revenue growth."
>       }
>     ],
>     "input_masking": {
>       "message": "Input to LLM is masked successfully.",
>       "data": {
>         "masked_template": [
>           {
>             "role": "user",
>            "content": "Summarize then following CV in 10 sentences: MASKED_PERSON_1 \n MASKED_PHONE_NUMBER_1 \n MASKED_EMAIL_1 \n\n Highlights \n - Strategic and financial planning expert \n - Accurate forecasting \n - Process implementation \n - Staff leadership and development \n - Business performance improvement \n - Proficient in SAP, Excel VBA\n\n Education \n Master of Science: Finance - 2014 \n Harvard University, Boston \n\n Bachelor of Science: Finance - 2011 \n Harvard University, Boston \n\n\n Certifications \n Certified Management Accountant \n\n\n Summary \n Skilled Financial Manager adept at increasing work process efficiency and profitability through functional and technical analysis. Successful at advising large corporations, small businesses, and individual clients. Areas of expertise include asset allocation, investment strategy, and risk management. \n\n\n Experience \n Finance Manager - 09/2016 to 05/2018 \n MASKED_ORG_1, MASKED_LOCATION_1 \n - Manage the modelling, planning, and execution of all financial processes. \n - Carry short and long-term custom comprehensive financial strategies to reach company goals. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Research market trends and surveys and use information to stimulate business. \n\n Finance Manager - 09/2013 to 05/2016 \n MASKED_ORG_2, MASKED_LOCATION_2 \n - Drafted executive analysis reports highlighting business issues, potential risks, and profit opportunities. \n - Recommended innovative alternatives to generate revenue and reduce unnecessary costs. \n - Employed advanced deal analysis, including hands-on negotiations with potential investors. \n - Analysed market trends and surveys and used information to revenue growth."
>         ]
>       }
>     },
>     "llm": {
>       "id": "chatcmpl-A5veOHbkabo04FugU7ysHeWeH7ZZC",
>       "object": "chat.completion",
>       "created": 1725976612,
>       "model": "gpt-4",
>       "choices": [
>         {
>           "index": 0,
>           "message": {
>             "role": "assistant",
>             "content": "MASKED_PERSON_1 is a skilled Financial Manager with expertise in strategic and financial planning, accurate forecasting, process implementation, staff leadership and development, and business performance improvement. They are proficient in SAP and Excel VBA. They hold a Master of Science in Finance from Harvard University and are a Certified Management Accountant. Their experience includes advising large corporations, small businesses, and individual clients on asset allocation, investment strategy, and risk management. They have worked as a Finance Manager for MASKED_ORG_1 and MASKED_ORG_2, where they managed financial processes, implemented financial strategies, recommended cost-saving measures, and conducted advanced deal analysis. They also have experience in researching market trends to stimulate business growth."
>           },
>           "finish_reason": "stop"
>         }
>       ],
>       "usage": {
>         "completion_tokens": 147,
>         "prompt_tokens": 378,
>         "total_tokens": 525
>       }
>     }
>   },
>   "orchestration_result": {
>     "id": "chatcmpl-A5veOHbkabo04FugU7ysHeWeH7ZZC",
>     "object": "chat.completion",
>     "created": 1725976612,
>     "model": "gpt-4",
>     "choices": [
>       {
>         "index": 0,
>         "message": {
>           "role": "assistant",
>           "content": "Patrick Morgan is a skilled Financial Manager with expertise in strategic and financial planning, accurate forecasting, process implementation, staff leadership and development, and business performance improvement. They are proficient in SAP and Excel VBA. They hold a Master of Science in Finance from Harvard University and are a Certified Management Accountant. Their experience includes advising large corporations, small businesses, and individual clients on asset allocation, investment strategy, and risk management. They have worked as a Finance Manager for M&K Group and Ago Group, where they managed financial processes, implemented financial strategies, recommended cost-saving measures, and conducted advanced deal analysis. They also have experience in researching market trends to stimulate business growth."
>         },
>         "finish_reason": "stop"
>       }
>     ],
>     "usage": {
>       "completion_tokens": 147,
>       "prompt_tokens": 378,
>       "total_tokens": 525
>     }
>   }
> }
> ```

When the grounding module is used, the masking module also supports masking of the grounding input before retrieval. By default, this feature is disabled. To enable it the parameter `mask_grounding_input` in the `masking_module_config` can be used as follows:

> ### Sample Code:  
> ```
> {
>   "orchestration_config": {
>     "module_configurations": {
>       "masking_module_config": {
>         "masking_providers": [
>           {
>             "type": "sap_data_privacy_integration",
>             "method": "pseudonymization",
>             "entities": [
>               {"type": "profile-person"},
>               {"type": "profile-email"}
>             ],
>             "mask_grounding_input": {"enabled": true}
>           }
>         ]
>         ...
>       }
>       ...
>     }
>   }
> }
> ```



<a name="loio592c570f22734ec5ba7881a0aeb49c50__section_xd2_fnt_nfc"/>

## Configuring Replacement Methods

You can configure the replacement method for each entity in the `masking_module_config`. The following methods are supported:

-   `fabricated_data`: Replaces the entity with a randomly generated value of the same type. For example, a person's name might be replaced with another name, and a phone number with a different phone number.

-   `constant`: Replaces the entity with a specified constant value.

    -   In anonymization, the constant value is used directly without any modification \(for example, `MASKED_PERSON`\).
    -   In pseudonymization, the constant is appended with an incrementing number to ensure uniqueness \(for example, `MASKED_PERSON_1`, `MASKED_PERSON_2`\).


If no replacement strategy is specified, the default `constant` replacement method is used with a default constant value \(for example, `MASKED_PERSON` for person entities\).

The following example shows code for fabricated data replacement:

```
"entities": [
  {
    "type": "profile-person",
    "replacement_strategy": {
      "method": "fabricated_data"
    }
  }
]
```

The following example shows code for constant replacement with a custom value:

```
"entities": [
  {
    "type": "profile-person",
    "replacement_strategy": {
      "method": "constant",
      "value": "PERSON_REDACTED"
    }
  }
]
```



### Using Custom Entities

In addition to the standard entity types, you can define custom entities using regular expressions. This allows you to mask specific patterns in your data that are not covered by the standard entity types. Custom entities require specifing the `constant` replacement strategy.

The following example shows code for constant replacement with a custom entity:

```
"entities": [
  {
    "regex": "[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\\.[a-zA-Z0-9-.]+",
    "replacement_strategy": {
      "method": "constant",
      "value": "REDACTED_EMAIL"
    }
  }
]
```

In this example, the regular expression `[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\\.[a-zA-Z0-9-.]+` is used to identify email addresses. The identified email addresses will be replaced with `REDACTED_EMAIL_1`, `REDACTED_EMAIL_2`, and so on.

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](libraries-and-sdks-499309d.md "Explore additional SDKs and libraries that you can use with SAP AI Core.")

