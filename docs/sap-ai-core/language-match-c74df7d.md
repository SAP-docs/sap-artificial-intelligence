<!-- loioc74df7d1d2b64d22aeaaada114415656 -->

# Language Match



## Context

This metric determines whether LLM generated content is in the language required.

For more information about supported languages and their corresponding codes, see [Supported Languages](language-match-c74df7d.md#loioc74df7d1d2b64d22aeaaada114415656__table_rtw_ngh_1fc).

The following external libraries are used:

-   lingua-py \(Apache-2.0 License\). For more information, see [Lingua-py](https://github.com/pemistahl/lingua-py?tab=readme-ov-file#4-which-languages-are-supported)
-   hanzidentifier \(MIT\) [Hanzidentifier](https://github.com/tsroten/hanzidentifier)

Language match uses the following evaluation flow:

1.  Use lingua-py to check the language
2.  If lang\_code not Chinese \(simplified/traditional\), match with user provided language code
3.  Else run with hanzidentifier \(zh\_TW/zh\_CN\) and match with user provided language code



## Procedure

Provide the code for the language you want to match.

-   Provide an entry on a single row that will be applied to all rows.
-   Provide an entry for each row individually.

For more information on available languages and their corresponding codes, see [Supported Languages](language-match-c74df7d.md#loioc74df7d1d2b64d22aeaaada114415656__table_rtw_ngh_1fc).

The metric returns `true` or `false` to indicate LLM output matches the given language. For example:

> ### Sample Code:  
> ```
> 
> {
>     "text": "LLM response, preferably long text",
>     "language": "en"
> }
> 
> ```

> ### Output Code:  
> ```
> True
> ```

<a name="concept_dvz_jlh_1fc"/>

<!-- concept\_dvz\_jlh\_1fc -->

## Supported Languages


<table>
<tr>
<th valign="top">

Language

</th>
<th valign="top">

iso\_code\_639\_1

</th>
</tr>
<tr>
<td valign="top">

AFRIKAANS

</td>
<td valign="top">

'AF'

</td>
</tr>
<tr>
<td valign="top">

ALBANIAN

</td>
<td valign="top">

'SQ'

</td>
</tr>
<tr>
<td valign="top">

ARABIC

</td>
<td valign="top">

'AR'

</td>
</tr>
<tr>
<td valign="top">

ARMENIAN

</td>
<td valign="top">

'HY'

</td>
</tr>
<tr>
<td valign="top">

AZERBAIJANI

</td>
<td valign="top">

'AZ'

</td>
</tr>
<tr>
<td valign="top">

BASQUE

</td>
<td valign="top">

'EU'

</td>
</tr>
<tr>
<td valign="top">

BELARUSIAN

</td>
<td valign="top">

'BE'

</td>
</tr>
<tr>
<td valign="top">

BENGALI

</td>
<td valign="top">

'BN'

</td>
</tr>
<tr>
<td valign="top">

BOKMAL

</td>
<td valign="top">

'NB'

</td>
</tr>
<tr>
<td valign="top">

BULGARIAN

</td>
<td valign="top">

'BG'

</td>
</tr>
<tr>
<td valign="top">

CATALAN

</td>
<td valign="top">

'CA'

</td>
</tr>
<tr>
<td valign="top">

CHINESE

</td>
<td valign="top">

'ZH'

</td>
</tr>
<tr>
<td valign="top">

SIMPLIFIED CHINESE

</td>
<td valign="top">

'ZH\_CN'

</td>
</tr>
<tr>
<td valign="top">

TRADITIONAL CHINESE

</td>
<td valign="top">

'ZH\_TW'

</td>
</tr>
<tr>
<td valign="top">

CROATIAN

</td>
<td valign="top">

'HR'

</td>
</tr>
<tr>
<td valign="top">

CZECH

</td>
<td valign="top">

'CS'

</td>
</tr>
<tr>
<td valign="top">

DANISH

</td>
<td valign="top">

'DA'

</td>
</tr>
<tr>
<td valign="top">

DUTCH

</td>
<td valign="top">

'NL'

</td>
</tr>
<tr>
<td valign="top">

ENGLISH

</td>
<td valign="top">

'EN'

</td>
</tr>
<tr>
<td valign="top">

ESPERANTO

</td>
<td valign="top">

'EO'

</td>
</tr>
<tr>
<td valign="top">

ESTONIAN

</td>
<td valign="top">

'ET'

</td>
</tr>
<tr>
<td valign="top">

FINNISH

</td>
<td valign="top">

'FI'

</td>
</tr>
<tr>
<td valign="top">

FRENCH

</td>
<td valign="top">

'FR'

</td>
</tr>
<tr>
<td valign="top">

GANDA

</td>
<td valign="top">

'LG'

</td>
</tr>
<tr>
<td valign="top">

GEORGIAN

</td>
<td valign="top">

'KA'

</td>
</tr>
<tr>
<td valign="top">

GERMAN

</td>
<td valign="top">

'DE'

</td>
</tr>
<tr>
<td valign="top">

GREEK

</td>
<td valign="top">

'EL'

</td>
</tr>
<tr>
<td valign="top">

GUJARATI

</td>
<td valign="top">

'GU'

</td>
</tr>
<tr>
<td valign="top">

HEBREW

</td>
<td valign="top">

'HE'

</td>
</tr>
<tr>
<td valign="top">

HINDI

</td>
<td valign="top">

'HI'

</td>
</tr>
<tr>
<td valign="top">

HUNGARIAN

</td>
<td valign="top">

'HU'

</td>
</tr>
<tr>
<td valign="top">

ICELANDIC

</td>
<td valign="top">

'IS'

</td>
</tr>
<tr>
<td valign="top">

INDONESIAN

</td>
<td valign="top">

'ID'

</td>
</tr>
<tr>
<td valign="top">

IRISH

</td>
<td valign="top">

'GA'

</td>
</tr>
<tr>
<td valign="top">

ITALIAN

</td>
<td valign="top">

'IT'

</td>
</tr>
<tr>
<td valign="top">

JAPANESE

</td>
<td valign="top">

'JA'

</td>
</tr>
<tr>
<td valign="top">

KAZAKH

</td>
<td valign="top">

'KK'

</td>
</tr>
<tr>
<td valign="top">

KOREAN

</td>
<td valign="top">

'KO'

</td>
</tr>
<tr>
<td valign="top">

LATIN

</td>
<td valign="top">

'LA'

</td>
</tr>
<tr>
<td valign="top">

LATVIAN

</td>
<td valign="top">

'LV'

</td>
</tr>
<tr>
<td valign="top">

LITHUANIAN

</td>
<td valign="top">

'LT'

</td>
</tr>
<tr>
<td valign="top">

MACEDONIAN

</td>
<td valign="top">

'MK'

</td>
</tr>
<tr>
<td valign="top">

MAORI

</td>
<td valign="top">

'MI'

</td>
</tr>
<tr>
<td valign="top">

MARATHI

</td>
<td valign="top">

'MR'

</td>
</tr>
<tr>
<td valign="top">

MONGOLIAN

</td>
<td valign="top">

'MN'

</td>
</tr>
<tr>
<td valign="top">

NYNORSK

</td>
<td valign="top">

'NN'

</td>
</tr>
<tr>
<td valign="top">

PERSIAN

</td>
<td valign="top">

'FA'

</td>
</tr>
<tr>
<td valign="top">

POLISH

</td>
<td valign="top">

'PL'

</td>
</tr>
<tr>
<td valign="top">

PORTUGUESE

</td>
<td valign="top">

'PT'

</td>
</tr>
<tr>
<td valign="top">

PUNJABI

</td>
<td valign="top">

'PA'

</td>
</tr>
<tr>
<td valign="top">

ROMANIAN

</td>
<td valign="top">

'RO'

</td>
</tr>
<tr>
<td valign="top">

RUSSIAN

</td>
<td valign="top">

'RU'

</td>
</tr>
<tr>
<td valign="top">

SERBIAN

</td>
<td valign="top">

'SR'

</td>
</tr>
<tr>
<td valign="top">

SHONA

</td>
<td valign="top">

'SN'

</td>
</tr>
<tr>
<td valign="top">

SLOVAK

</td>
<td valign="top">

'SK'

</td>
</tr>
<tr>
<td valign="top">

SLOVENE

</td>
<td valign="top">

'SL'

</td>
</tr>
<tr>
<td valign="top">

SOMALI

</td>
<td valign="top">

'SO'

</td>
</tr>
<tr>
<td valign="top">

SOTHO

</td>
<td valign="top">

'ST'

</td>
</tr>
<tr>
<td valign="top">

SPANISH

</td>
<td valign="top">

'ES'

</td>
</tr>
<tr>
<td valign="top">

SWAHILI

</td>
<td valign="top">

'SW'

</td>
</tr>
<tr>
<td valign="top">

SWEDISH

</td>
<td valign="top">

'SV'

</td>
</tr>
<tr>
<td valign="top">

TAGALOG

</td>
<td valign="top">

'TL'

</td>
</tr>
<tr>
<td valign="top">

TAMIL

</td>
<td valign="top">

'TA'

</td>
</tr>
<tr>
<td valign="top">

TELUGU

</td>
<td valign="top">

'TE'

</td>
</tr>
<tr>
<td valign="top">

THAI

</td>
<td valign="top">

'TH'

</td>
</tr>
<tr>
<td valign="top">

TSONGA

</td>
<td valign="top">

'TS'

</td>
</tr>
<tr>
<td valign="top">

TSWANA

</td>
<td valign="top">

'TN'

</td>
</tr>
<tr>
<td valign="top">

TURKISH

</td>
<td valign="top">

'TR'

</td>
</tr>
<tr>
<td valign="top">

UKRAINIAN

</td>
<td valign="top">

'UK'

</td>
</tr>
<tr>
<td valign="top">

URDU

</td>
<td valign="top">

'UR'

</td>
</tr>
<tr>
<td valign="top">

VIETNAMESE

</td>
<td valign="top">

'VI'

</td>
</tr>
<tr>
<td valign="top">

WELSH

</td>
<td valign="top">

'CY'

</td>
</tr>
<tr>
<td valign="top">

XHOSA

</td>
<td valign="top">

'XH'

</td>
</tr>
<tr>
<td valign="top">

YORUBA

</td>
<td valign="top">

'YO'

</td>
</tr>
<tr>
<td valign="top">

ZULU

</td>
<td valign="top">

'ZU'

</td>
</tr>
</table>

