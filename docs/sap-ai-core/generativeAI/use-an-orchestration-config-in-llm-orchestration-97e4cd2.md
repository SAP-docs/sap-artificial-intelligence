<!-- loio97e4cd20391b42729df802ef9f4484f9 -->

# Use an Orchestration Config in LLM Orchestration



## Prerequisites

You have created an orchestration config. For more information, see [Create an Orchestration Config \(Imperative\)](create-an-orchestration-config-imperative-2f27317.md)and [Create an Orchestration Config \(Declarative\)](create-an-orchestration-config-declarative-508e66f.md).



## Context

Orchestration configs can be used in LLM Orchestration completion requests in the following ways:

1.  **Inline configuration**: Define the configuration directly in the request
2.  **Reference by ID**: Reference a stored config by its unique ID
3.  **Reference by name, scenario, and version**: Reference a stored config by its metadata



## Procedure

You can reference orchestration configs using the following methods:

Set the following in the headers:

-   `ORCHESTRATION_DEPLOYMENT_URL`: your orchestration deployment url. For more information, see [Get An Orchestration Deployment URL](get-an-orchestration-deployment-url-ec7c703.md).
-   `{{access_token}}`: Your access token for SAP AI Core



### Method 1: Reference Orchestration Config by ID

Send a POST request to the LLM Orchestration completion endpoint with a config reference by ID.

```
curl -X POST "$ORCHESTRATION_DEPLOYMENT_URL/v2/completion" \
     -H "Authorization: Bearer <your_auth_token>" \
     -H "Content-Type: application/json" \
     -d '{
  "config_ref": {
    "id": "<orchestrationConfigId>"
  },
  "placeholder_values": {
    "userQuery": "What are the benefits of SAP AI Core?",
    "groundingInput": "How many minimum annual leave days do SAP full-time employees have?"
  }
}'

```

> ### Note:  
> Placeholder keys must match the stored orchestration config exactly, and are case-sensitive.



### Method 2: Reference Orchestration Config by Name, Scenario, and Version

Send a POST request to the LLM Orchestration completion endpoint with a config reference by metadata.

```
curl -X POST "$ORCHESTRATION_DEPLOYMENT_URL/v2/completion" \
     -H "Authorization: Bearer <your_auth_token>" \
     -H "Content-Type: application/json" \
     -d '{
  "config_ref": {
    "scenario": "customer-support",
    "name": "example-orchestration-config",
    "version": "0.0.1"
  },
  "placeholder_values": {
    "userQuery": "What are the benefits of SAP AI Core?",
    "groundingInput": "How many minimum annual leave days do SAP full-time employees have?"
  },
  "messages_history": [
    {
      "role": "system",
      "content": "You are helping with technical integration questions."
    }
  ]
}'

```

> ### Note:  
> Placeholder keys must match the stored orchestration config exactly, and are case-sensitive.



### Method 3: Inline Configuration \(for comparison\)

You can also use orchestration configurations inline without storing them first.

```
curl -X POST "$ORCHESTRATION_DEPLOYMENT_URL/v2/completion" \
     -H "Authorization: Bearer <your_auth_token>" \
     -H "Content-Type: application/json" \
     -d '{
           "config": {
             "modules": {
               "prompt_templating": {
                 "prompt": {
                   "template": [
                     {
                       "role": "user",
                       "content": "{{?userQuery}}"
                     }
                   ]
                 },
                 "model": {
                   "name": "<model>"
                 }
               }
             }
           },
           "placeholder_values": {
             "userQuery": "What is SAP AI Core?"
           }
         }'

```

> ### Note:  
> Use stored orchestration configs \(methods 1 and 2\) when you have reusable configurations that multiple applications or workflows need to access. Use inline configurations \(method 3\) for one-off or experimental requests.

> ### Note:  
> When referencing orchestration configs in LLM Orchestration:
> 
> -   Reference by ID provides immutability meaning that the config behind the ID will never change
> -   Reference by name, scenario, and version provides flexibility meaning that you get the latest iteration of that version

