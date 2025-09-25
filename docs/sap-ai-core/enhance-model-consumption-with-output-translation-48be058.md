<!-- loio48be058d01bd4df2a82e5430561e6f44 -->

# Enhance Model Consumption with Output Translation

To configure output translation, add an `translation` section to the `modules` of your `config`.

For example:

> ### Sample Code:  
> ```
> {
> "config": {
>   "modules": {
>     ...
>     "translation": {
>                 "output": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "source_language": "en-US",
>                         "target_language": "de-DE"
>                     }
>                 }
>     ...
>   }
>   ...
> }
> }
> ```

The `translation` must object must specify the keys:

-   `type`: specifying the translation service being called.

    The following values are supported:

    -   `sap_document_translation`

-   `config`: containing the parameters that are sent to the service to configure translation.

    The following parameters are supported:

    -   `source_language` \(optional\)
    -   `target_language` \(mandatory\)


The source language is the language of the input text. If no source language is specified, the SAP Translation Service will try to detect the source language.

> ### Remember:  
> For texts containing multiple languages, the service might be unable to detect the source language.

The target language is the language that the input will be translated to, and is mandatory.

For more information on possible languages and translation pairs, see [Supported Languages](https://help.sap.com/docs/translation-hub/sap-translation-hub/supported-languages-6854bbb1bd824ffebc3a097a7c0fd45d) of the document translation service in SAP Translation Hub.



<a name="loio48be058d01bd4df2a82e5430561e6f44__section_vnb_f5h_1fc"/>

## Example

The following example shows a summarizing support assistant and uses the translation module to translate a support request summary into Spanish for a Spanish speaking support team.

> ### Sample Code:  
> ```
> {
>   "config": {
>     "modules": {
>       "prompt_templating": {
>         "messages_history": [
>         {
>         "role": "system",
>         "content": "You are a helpful support assistant. Your task is to summarize a given support request for the human support team in Germany."
>         },          
>         {
>         "role": "user",
>         "content": "Support Request: '''{{?support-request}}'''"
>         }
>         ]
>       },
>       "model": {
>         "name": "gpt-4o-mini"
>         },
>       "translation": {
>         "type": "sap_document_translation",
>         "config": {
>           "target_language": "de-DE"
>           }
>         }
>       }
>     }
>   },
>   "placeholder_values": {
>      "support-request": "Subject: Order #1234567890 Delayed - John Johnson Message: Hi I'm writing to inquire about the status of my order +1234567890. It was supposed to arrive yesterday but hasn't shown up. My Name is John Johnson, and the delivery address is 125 Cole Meadows Drive Palo Alto, California 94301. Please advice on the expected delivery date via +1 505802 2172. Thanks!"
> }
> ```

