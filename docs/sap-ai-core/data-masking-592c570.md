<!-- loio592c570f22734ec5ba7881a0aeb49c50 -->

# Data Masking

In the following example we use the data masking module to anonymize persons, organisations, and contact information in the input.

The entries "Harvard University" and "Boston" in the allowlist will not be masked.

In this case, the input will be masked before the call to the LLM. However data can not be unmasked in the LLM output.

> ### Sample Code:  
> ```
> 
> curl --request POST $ORCH_DEPLOYMENT_URL/completion \
>     --header 'content-type: application/json' \
>     --header "Authorization: Bearer $TOKEN" \
>     --header "ai-resource-group: $RESOURCE_GROUP" \
>     --data-raw '{
>   "orchestration_config": {
>     "module_configurations": {
>       "templating_module_config": {
>         "template": [
>           {
>             "role": "user",
>             "content": "Summarize the following CV in 10 sentences: {{?orgCV}}"
>           }
>         ],
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

As the response shows, the configured entities are masked by the data masking module before being sent to the LLM. The LLM operates on the masked data and is still able to provide a summary.

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

Using `"method": "pseudonymization"` instead of `"method": "anonymization"` in the masking module configuration will pseudonymize the data before sending it to the LLM. Additionally the LLM response is checked for any data that can be unmasked before sending out the final response.

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

