<!-- loio8b87002906ee446cbcbeb98cd95e1ea3 -->

# Data Masking

The data masking module is optional and serves to anonymize or pseudonymize personally identifiable information from the input for selected entities.

There are two ways in which you can mask data:

-   Anonymization replaces personally identifiable information in chosen categories with a `MASKED_ENTITY` placeholder. Anonymized data can't be unmasked because the original data isn't retained.
-   Pseudonymization substitutes personally identifiable information in selected categories with a `MASKED_ENTITY_ID` placeholder. Pseudonymized data can be unmasked in the response.

The module currently supports the following anonymization services:

-   SAP Data Privacy Integration - Anonymization


**SAP Data Privacy Integration - Anonymization**

SAP Data Privacy Integration - Anonymization service recognizes the following entity categories:


<table>
<tr>
<th valign="top">

Entity

</th>
<th valign="top">

Description

</th>
<th valign="top">

Scope

</th>
</tr>
<tr>
<td valign="top">

profile-person

</td>
<td valign="top">

Person Name

</td>
<td valign="top">

English

</td>
</tr>
<tr>
<td valign="top">

profile-org

</td>
<td valign="top">

Organization

</td>
<td valign="top">

SAP customers + Fortune 1000 companies

</td>
</tr>
<tr>
<td valign="top">

profile-university

</td>
<td valign="top">

University

</td>
<td valign="top">

Organization identified as a public University

</td>
</tr>
<tr>
<td valign="top">

profile-location

</td>
<td valign="top">

Location

</td>
<td valign="top">

United States

</td>
</tr>
<tr>
<td valign="top">

profile-phone

</td>
<td valign="top">

Phone Number

</td>
<td valign="top">

International phone numbers in the following format: +country/region code, any prefix and phone number

</td>
</tr>
<tr>
<td valign="top">

profile-address

</td>
<td valign="top">

U.S. Physical Addresses

</td>
<td valign="top">

United States

</td>
</tr>
<tr>
<td valign="top">

profile-email

</td>
<td valign="top">

E-mail addresses

</td>
<td valign="top">

E-mail addresses

</td>
</tr>
<tr>
<td valign="top">

profile-sapids-internal

</td>
<td valign="top">

SAP Staff User ID Numbers

</td>
<td valign="top">

User ID: Sequence of characters that starts with either C, I, or D followed by 6-8 digits.

</td>
</tr>
<tr>
<td valign="top">

profile-sapids-public

</td>
<td valign="top">

Public SAP Accounts

</td>
<td valign="top">

S-user ID: Sequence of characters that starts with S and followed by 6-11 digits.

P-user ID: Sequence of characters that starts with P followed by 10 digits.

</td>
</tr>
<tr>
<td valign="top">

profile-url

</td>
<td valign="top">

URL

</td>
<td valign="top">

Only anonymize URLs that can be accessed by the user

</td>
</tr>
<tr>
<td valign="top">

profile-username-password

</td>
<td valign="top">

Username and Passwords

</td>
<td valign="top">

Detected if words similar to user, user name, pass, passwords, and so on.

</td>
</tr>
<tr>
<td valign="top">

profile-nationalid

</td>
<td valign="top">

National ID Number

</td>
<td valign="top">

20+ countries/regions \(for example, E.U., South America\)

</td>
</tr>
<tr>
<td valign="top">

profile-iban

</td>
<td valign="top">

International Bank Account Number \(IBAN\)

</td>
<td valign="top">

70+ countries/regions \(E.U., Middle East, South America\)

</td>
</tr>
<tr>
<td valign="top">

profile-ssn

</td>
<td valign="top">

Social Security Number \(SSN\)/Social Insurance Number \(SIN\)

</td>
<td valign="top">

United States and Canada

</td>
</tr>
<tr>
<td valign="top">

profile-credit-card-number

</td>
<td valign="top">

Credit Card Number

</td>
<td valign="top">

Global

</td>
</tr>
<tr>
<td valign="top">

profile-passport

</td>
<td valign="top">

Passport Number

</td>
<td valign="top">

30+ countries/regions \(for example, E.U., Asia Pacific, North America\)

</td>
</tr>
<tr>
<td valign="top">

profile-driverlicense

</td>
<td valign="top">

Driver's License

</td>
<td valign="top">

30+ countries/regions \(for example, E.U., Asia Pacific\)

</td>
</tr>
<tr>
<td valign="top">

profile-nationality

</td>
<td valign="top">

Nationality

</td>
<td valign="top">

190+ country/region names, official country/region names, and country/region codes

</td>
</tr>
<tr>
<td valign="top">

profile-religious-group

</td>
<td valign="top">

Religious Group

</td>
<td valign="top">

200+ religious groups

</td>
</tr>
<tr>
<td valign="top">

profile-political-group

</td>
<td valign="top">

Political Parties or Groups

</td>
<td valign="top">

100+ political parties or groups

</td>
</tr>
<tr>
<td valign="top">

profile-pronouns-gender

</td>
<td valign="top">

Gender pronoun

</td>
<td valign="top">

Global

</td>
</tr>
<tr>
<td valign="top">

profile-gender

</td>
<td valign="top">

Gender

</td>
<td valign="top">

Global

</td>
</tr>
<tr>
<td valign="top">

profile-sexual-orientation

</td>
<td valign="top">

Sexual Orientation

</td>
<td valign="top">

Global

</td>
</tr>
<tr>
<td valign="top">

profile-trade-union

</td>
<td valign="top">

Trade Union

</td>
<td valign="top">

Global

</td>
</tr>
<tr>
<td valign="top">

profile-sensitive-data

</td>
<td valign="top">

Nationality, Religious\_Group, Gender, Political\_Group, pronoun gender, ethnicity, sexual orientation, Trade union

</td>
<td valign="top">

Mixed

</td>
</tr>
</table>

> ### Caution:  
> The masking service can obscure personally identifiable information in prompts. However, since it relies on automated detection mechanisms, it can't guarantee that all such information is identified and masked.
> 
> Anonymization replaces personally identifiable information in an irreversible way. As a result, context can be lost, which can limit the model's ability to process the input. For instance, if tasked with writing a story about Michael and Donna, anonymization of profile-person results in a story about `MASKED_PERSON` and `MASKED_PERSON`, making it impossible to distinguish between the two.

-   **[Enhancing Model Consumption with Data Masking](enhancing-model-consumption-with-data-masking-592c570.md "")**  


