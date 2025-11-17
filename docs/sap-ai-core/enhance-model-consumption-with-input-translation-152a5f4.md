<!-- loio152a5f4796f9493d98323786571356bf -->

# Enhance Model Consumption with Input Translation

To configure translation, add a `translation` section to the `modules` of your `config`.



## Configuration Example

> ### Sample Code:  
> ```
>     "config": {
>         "modules": {
>             ...
>             "translation": {
>                 "input": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "source_language": "de-DE",
>                         "target_language": "en-US"
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

The `translation` object must specify the keys::

-   `type`: the translation service being called.

    The following values are supported:

    -   `sap_document_translation`

-   `config`: parameters sent to the service to configure translation.

    The following parameters are supported:

    -   `source_language` \(optional\): the language of the input text. If no source language is specified, the SAP Document Translation Service automatically detects the source language.
    -   `target_language` \(mandatory\): the language to translate the input to.
    -   `apply_to` \(optional\): specify which parts of the input to translate for granular control. For more information , see [Selective Translation with apply\_to](enhance-model-consumption-with-input-translation-152a5f4.md#loio152a5f4796f9493d98323786571356bf__section_rck_4gp_2hc).



> ### Note:  
> For texts containing multiple languages, the service might be unable to detect the source language accurately.



## Supported Languages

For more information on supported languages and translation pairs, see [Supported Languages](https://help.sap.com/docs/translation-hub/sap-translation-hub/supported-languages-6854bbb1bd824ffebc3a097a7c0fd45d) of the document translation service in SAP Translation Hub.



<a name="loio152a5f4796f9493d98323786571356bf__section_rck_4gp_2hc"/>

## Selective Translation with `apply_to`

The `apply_to` parameter enables precise control over which content gets translated, allowing you to translate only specific parts of your input while leaving others unchanged.



### Configuration Properties

Each entry in the `apply_to` array supports the following:

-   `category` \(required\): the content type to select for translation

    Supported values:

    -   `placeholders`: translate specific placeholder values from `placeholder_values` and `grounding.placeholders.output`
    -   `template_roles`: translate template messages with specific message roles

-   `items` \(required\): an array of specific items within the category to translate

    -   For `category: placeholders`: array of placeholder keys
        -   Examples: `["user_input", "grounding_input", "grounding_output", "custom_parameter"]`

    -   For `category: template_roles`: Array of message role names from your template.
        -   Supported values: `["user", "assistant", "system", "developer", "tool"]`
        -   These correspond to the `role` field in your message objects


-   `source_language` \(optional\): The source language for this entry. If not provided, the service automatically detects the source language.


> ### Tip:  
> When using automatic source language detection, avoid grouping items with different languages in the same `apply_to` entry, as this may lead to incorrect translation results. Use separate entries for items in different languages.

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
>                                 "category": "placeholders",
>                                 "items": [
>                                     "user_input"
>                                 ],
>                                 "source_language": "de-DE"
>                             },
>                             {
>                                 "category": "placeholders",
>                                 "items": [
>                                     "grounding_output"
>                                 ]
>                             },
>                             {
>                                 "category": "template_roles",
>                                 "items": [
>                                     "user",
>                                     "assistant"
>                                 ]
>                             }
>                         ]
>                     }
>                 }
>             }
>         }
>     }
> }
>  ```
> ```



## Chat History Control

By default, chat history messages are translated. To avoid repeating the translation of chat history messages that have already been translated, set `translation.input.config.translate_messages_history` to `false`.



<a name="loio152a5f4796f9493d98323786571356bf__section_vnb_f5h_1fc"/>

## Examples



### Example 1: Customer Support Request Translation

The following example shows a summarizing support assistant and uses the translation module to translate a support request message from German to English before sending it to the LLM for summarization.

> ### Sample Code:  
> ```
> {
>     "config": {
>         "modules": {
>             "prompt_templating": {
>                 "messages_history": [
>                     {
>                         "role": "system",
>                         "content": "You are a helpful support assistant. Your task is to summarize a given support request for the human support team.\nYou proceed as follows: Summarize the issue for the human support team. Provide your answer in the following format:\n - Sentiment: [your sentiment analysis]\n - Key Theme: [theme of the support issue]\n - Contact: [any contact information available in the issue]"
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
>                 "input": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "source_language": "de-DE",
>                         "target_language": "en-US"
>                     }
>                 }
>             }
>         }
>     },
>     "placeholder_values": {
>         "support-request": "Subject: Bestellung #1234567890 Verspätet - John Johnson Nachricht: Hallo, ich schreibe ihnen um mich nach dem Status meiner Bestellung mit der Bestellnr. +1234567890 zu erkundigen. Die Lieferung war eigentlich für gestern geplant, ist bisher jedoch nicht erfolgt. Mein Name ist John Johnson und meine Lieferadresse lautet 125 Cole Meadows Drive Palo Alto, California 94301. Bitte lassen Sie mich per Telefon unter der Nummer +1 505802 2172 wissen, wann ich mit meiner Lieferung rechnen kann. Danke!"
>     }
> }
>  ```
> ```



### Example 2: Study Guide with Selective Placeholder Translation

A study guide generator that translates specific input parameters while keeping others unchanged:

> ### Sample Code:  
> ```
>  {
>     "placeholder_values": {
>         "exam_type": "Abitur",
>         "topic": "Deutsche Literatur",
>         "num_questions": "5"
>     },
>     "config": {
>         "modules": {
>             "prompt_templating": {
>                 "prompt": {
>                     "template": [
>                         {
>                             "role": "system",
>                             "content": "You are an expert study coach creating clear, concise exam notes and practice questions."
>                         },
>                         {
>                             "role": "user",
>                             "content": "Generate a study guide for the {{?exam_type}} exam on {{?topic}}.\n\nInclude {{?num_questions}} practice questions."
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
>                                 "category": "placeholders",
>                                 "items": [
>                                     "exam_type",
>                                     "topic"
>                                 ],
>                                 "source_language": "de-DE"
>                             }
>                         ],
>                         "target_language": "en-US"
>                     }
>                 }
>             }
>         }
>     }
> }
> ```

