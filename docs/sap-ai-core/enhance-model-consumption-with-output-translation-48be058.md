<!-- loio48be058d01bd4df2a82e5430561e6f44 -->

# Enhance Model Consumption with Output Translation

Output translation translates LLM responses into your preferred language. This ensures the LLM can operate at peak performance in its strongest language while delivering responses in the format most useful to the user.

To configure output translation, add a `translation` section to the `modules` of your `config`.



## Configuration Example

> ### Sample Code:  
> ```
>  {
>     "config": {
>         "modules": {
>             ...
>             "translation": {
>                 "output": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "source_language": "en-US",
>                         "target_language": "de-DE"
>                     }
>                 }
>             }
>             ...
>         }
>     }
>     ...
> }
> ...
> ```



## Configuration Parameters

The `translation` must object must specify the keys:

-   `type`: the translation service being called

    The following values are supported:

    -   `sap_document_translation`

-   `config`: the parameters that are sent to the service to configure translation

-   `target_language` \(mandatory\): the output language

    The following values are supported:

    -   A language code string \(for example, "de-DE"\) for fixed target language

    -   A reference object to match the language of your input query. For more information, see [Automatic Target Language Inference](enhance-model-consumption-with-output-translation-48be058.md#loio48be058d01bd4df2a82e5430561e6f44__section_rkh_zkp_2hc).





## Supported Languages

For more information on supported languages and translation pairs, see [Supported Languages](https://help.sap.com/docs/translation-hub/sap-translation-hub/supported-languages-6854bbb1bd824ffebc3a097a7c0fd45d) of the document translation service in SAP Translation Hub.



<a name="loio48be058d01bd4df2a82e5430561e6f44__section_rkh_zkp_2hc"/>

## Automatic Target Language Inference

Output translation can automatically respond in the user's original language by referencing the detected source language from input translation. This is particularly useful if the user's language is not known in advance.

Instead of specifying a fixed target language, reference an `apply_to` item from your input translation. For more information, see [Selective Translation with apply\_to](enhance-model-consumption-with-input-translation-152a5f4.md#loio152a5f4796f9493d98323786571356bf__section_rck_4gp_2hc).

> ### Sample Code:  
> ```
> {
>     "config": {
>         "modules": {
>             "translation": {
>                 "input": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "target_language": "en-US",
>                         "apply_to": [
>                             {
>                                 "category": "template_roles",
>                                 "items": [
>                                     "user"
>                                 ]
>                             }
>                         ]
>                     }
>                 },
>                 "output": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "source_language": "en-US",
>                         "target_language": {
>                             "category": "template_roles",
>                             "items": [
>                                 "user"
>                             ]
>                         }
>                     }
>                 }
>             }
>         }
>     }
> }
> ```

> ### Restriction:  
> The reference must exactly match an existing `apply_to` entry from your input translation configuration. In the example above, the `target_language` object in the output translation matches the first element in the input translation's `apply_to` array.



<a name="loio48be058d01bd4df2a82e5430561e6f44__section_vnb_f5h_1fc"/>

## Examples



### Example 1: Basic Output Translation

The following example shows a summarizing support assistant and uses the translation module to translate a support request summary into German for a German-speaking support team.

> ### Sample Code:  
> ```
> {
>     "config": {
>         "modules": {
>             "prompt_templating": {
>                 "messages_history": [
>                     {
>                         "role": "system",
>                         "content": "You are a helpful support assistant. Your task is to summarize a given support request for the human support team in Germany."
>                     },
>                     {
>                         "role": "user",
>                         "content": "Support Request: '''{{?support-request}}'''"
>                     }
>                 ]
>             },
>             "model": {
>                 "name": "gpt-4o-mini"
>             },
>             "translation": {
>                 "output": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "source_language": "en-US",
>                         "target_language": "de-DE"
>                     }
>                 }
>             }
>         }
>     },
>     "placeholder_values": {
>         "support-request": "Subject: Order #1234567890 Delayed - John Johnson Message: Hi I'm writing to inquire about the status of my order +1234567890. It was supposed to arrive yesterday but hasn't shown up. My Name is John Johnson, and the delivery address is 125 Cole Meadows Drive Palo Alto, California 94301. Please advice on the expected delivery date via +1 505802 2172. Thanks!"
>     }
> }
> ```



### Example 2: Automatic Target Language Matching

A travel assistant that automatically responds in the same language as the input:

> ### Sample Code:  
> ```
> {
>     "config": {
>         "modules": {
>             "prompt_templating": {
>                 "prompt": {
>                     "template": [
>                         {
>                             "role": "system",
>                             "content": "You are a helpful travel assistant who gives clear and friendly planning advice."
>                         },
>                         {
>                             "role": "user",
>                             "content": "Ich möchte nächsten Monat nach Paris reisen. Kannst du mir bei der Planung helfen?"
>                         }
>                     ]
>                 },
>                 "model": {
>                     "name": "gpt-4o"
>                 }
>             },
>             "translation": {
>                 "input": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "apply_to": [
>                             {
>                                 "category": "template_roles",
>                                 "items": [
>                                     "user"
>                                 ]
>                             }
>                         ],
>                         "target_language": "en-US"
>                     }
>                 },
>                 "output": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "source_language": "en-US",
>                         "target_language": {
>                             "category": "template_roles",
>                             "items": [
>                                 "user"
>                             ]
>                         }
>                     }
>                 }
>             }
>         }
>     }
> }
> ```

