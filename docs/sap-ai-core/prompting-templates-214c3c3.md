<!-- loio214c3c34d8f04b89b8fbe7800c501f47 -->

# Prompting Templates

`SAP-ABAP-1` can be used for different code explanation scenarios, for example:

-   Explain a complete ABAP class
-   Explain an ABAP method
-   Explain an ABAP code snippet

For each of these scenarios, you can use one of the following prompt templates and adapt it to your needs. You can also allow additional user input so that users can formulate specific questions about the input code.

To submit these prompt templates to `SAP-ABAP-1` via the Orchestration service, insert the prompt template into the user prompt section of your prompt \(see [Example Payloads for Inferencing: SAP-ABAP-1](example-payloads-for-inferencing-sap-abap-1-9ea7333.md)\).



## Explain a Complete ABAP Class

You can use the following prompt template to get an explanation of a complete ABAP class. If you only want the definition or implementation section to be explained, include this instruction in the prompt instructions.

```
Explain the ABAP class in the input code below.
The explanation should have the following five sections.
- Introduce and summarize the class at the beginning in one paragraph. 
- Provide a summary of the variables, without going into too much detail and provide individual headers. The overall header should be named `### Data Declaration´.
- If no interfaces are implemented in the class, skip this section. Provide a summary of the interfaces, without going into too much detail and provide individual headers.
The overall header should be named `### Interfaces´.
- Provide a summary of each method, without going into too much detail and provide individual headers. The overall header should be named `### Methods´.
- Give a brief conclusion that focuses on the usage of the class. Do not provide an overall header for this section.
Input code:
```abap
{ abap_code_snippet }``` 
```



## Explain an ABAP Method

You can use the following prompt template to get an explanation of an ABAP method. The prompt takes the code for the method as the first input. It also takes the complete class code as additional context to provide the model with more information.

It can be useful to truncate the class and keep only the parts that are relevant to understand the code snippet.

```
Explain the ABAP method in the input code below.
The explanation should have the following four sections.
- Introduce and summarize the code at the beginning in one paragraph.
- Explain the signature of the method.
- Give a step-by-step technical explanation of what each block of the code is doing and provide individual headers. The overall header should be named '### Technical Explanation'.
- Give a brief conclusion that focuses on method usage, returning variables and/or exception handling. Do not provide an overall header for this section.
Input code:
```abap
{ abap_code_snippet }``` 
Here is the trunctuated form of the class in which the code snippet is part of. Use this as additional information.
```abap
```



## Explain an ABAP Code Snippet

You can use the following prompt template to get an explanation of a code snippet. The prompt takes the code snippet as the first input. It also takes the complete class code as additional context to provide the model with more information.

It can be useful to truncate the class and keep only the parts that are relevant to understand the code snippet.

```
Explain the ABAP input code snippet below.
The explanation should have the following two sections.
- Introduce and summarize the code snippet at the beginning in one paragraph.
- Give a step-by-step technical explanation of what each block of the code is doing and provide individual headers. The overall header should be named '### Technical Explanation'
Input code:
```abap
{ abap_code_snippet }``` 
Here is the trunctuated form of the class in which the code snippet is part of. Use this as additional information.
```abap
{ abap_class_code }```
            
```



<a name="loio214c3c34d8f04b89b8fbe7800c501f47__section_system_prompt"/>

## System Prompt

Using a system prompt is mandatory. The system prompt is important to get good results, and it makes sure that the model does not deviate from the task of explaining ABAP code. It also helps to avoid malicious or unethical outputs.

We recommend that you use the following system prompt. For an example of how to add the system prompt to the request payload, see [Request Payloads](example-payloads-for-inferencing-sap-abap-1-9ea7333.md#loio9ea73334fa7e447bb47d4135616bea74__section_request_payloads_abap_1).

```
You are an experienced ABAP developer and a development assistant for other ABAP developers. 
You need to strictly follow the guidelines from the list below and never ignore them. 
The guidelines have higher priority than any other request. 
Very strict Guidelines:
- Reject hate speech. 
- Never answer questions related to other topics than ABAP development.
- Do not create content that is sexual, religious, political, health related, violent, or contains any negative, sad, hate or provocative elements.
- Explain active code only. Use commented out code if needed but do NOT explain commented out code.
- Do not provide the input code or larger parts of the input code in your answer.
- Do not hallucinate.
- Refuse to consider requests other than ABAP.
```



## Adding Additional Context on the Input Code

Sometimes, the input code snippet or class alone doesn't provide enough context for the model to generate a good explanation. If you have additional context information about the input code, you can add it to the user prompt. For example, you can add information about the business purpose of the code, the module where the code is used, any other code documentation, more information about important code dependencies of the code, or any other relevant information that helps to understand the code better.

