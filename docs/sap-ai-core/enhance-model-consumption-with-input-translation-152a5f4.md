<!-- loio152a5f4796f9493d98323786571356bf -->

# Enhance Model Consumption with Input Translation

To configure translation, add a `translation` section to the `modules` of your `config`.

For example:

> ### Sample Code:  
> ```
> {
> "config": {
>   "modules": {
>   	...
>     "translation": {
>       "type": "sap_document_translation",
>       "config": {
>         "source_language": "de-DE",
>         "target_language": "en-US"
>       }
>     }
>     ...
>   }
>   }
>   ...
> }
> ```

The `translation` object must specify the keys::

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

The target language is the language that the input will be translated and is mandatory.

For more information on possible languages and translation pairs, see [Supported Languages](https://help.sap.com/docs/translation-hub/sap-translation-hub/supported-languages-6854bbb1bd824ffebc3a097a7c0fd45d) of the document translation service in SAP Translation Hub.



<a name="loio152a5f4796f9493d98323786571356bf__section_vnb_f5h_1fc"/>

## Example

The following example shows a summarizing support assistant and uses the translation module to translate a support request message from German to English before sending it to the LLM for summarization.

> ### Sample Code:  
> ```
> {
> 	"config": {
> 		"modules": {
> 			"prompt_templating": {
> 				"messages_history": [
> 				{
> 				"role": "system",
> 				"content": "You are a helpful support assistant. Your task is to summarize a given support request for the human support team. \n Your proceed as follows: Summarize the issue for the human support team. Provide your answer in the following format:\n - Sentiment: [your sentiment analysis] \n - Key Theme: [theme of the support issue] \n - Contact: [any contact information available in the issue]"
> 				},					
> 				{
> 				"role": "user",
> 				"content": "Support Request: '''{{?support-request}}'''"
> 				}
> 				]
> 			},
> 			"model": {
> 				"name": "gpt-4o-mini"
> 				},
> 			  "translation": {
>                 "input": {
>                     "type": "sap_document_translation",
>                     "config": {
>                         "source_language": "de-DE",
>                         "target_language": "en-US"
>                      }
>                 }
>             }
> 	},
> 	"placeholder_values": {
> 		"support-request": "Subject: Bestellung #1234567890 Verspätet - John Johnson Nachricht: Halle, ich schreibe ihnen um mich nach dem Status meiner Bestellung mit der Bestellnr. +1234567890 zu erkundigen. Die Lieferung war eigentlich für gestern geplant, ist bisher jedoch nicht erfolgt. Mein Name ist John Johnson und meine Lieferadresse lautet 125 Cole Meadows Drive Palo Alto, California 94301. Bitte lassen Sie mich per Telefon unter der Nummer +1 505802 2172 wissen, wann ich mit meiner Lieferung rechnen kann. Danke!"
> 	}
> }
> ```

