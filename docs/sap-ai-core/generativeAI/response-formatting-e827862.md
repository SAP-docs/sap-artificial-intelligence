<!-- loioe8278623b0584e6eafe46ce9b679af6a -->

# Response Formatting



You can define a schema for the response structure to follow. To do this, include a `response_format` field in your prompt template and populating it with details of your structure. `response_format` is an optional field.

For example:

```
{
    "name": "response-format-prompt-template",
    "version": "0.0.1",
    "scenario": "genai-optimizations",
    "spec": {
        "template": [
            {
                "role": "system",
                "content": "you are a helpful assistant"
            },
            {
                "role": "user",
                "content": "Giving the following message:\n---\n{{?input}}\n---\nExtract and return a json with the follwoing keys and values:\n- \"urgency\" as one of `high`, `medium`, `low`\n- \"sentiment\" as one of `negative`, `neutral`, `positive`\n- \"categories\" Create a dictionary with categories as keys and boolean values (True/False), \n  where the value indicates whether the category is one of the best matching support category tags from: \n  `emergency_repair_services`, `routine_maintenance_requests`, `quality_and_safety_concerns`, \n  `specialized_cleaning_services`, `general_inquiries`, `sustainability_and_environmental_practices`, \n  `training_and_support_requests`, `cleaning_services_scheduling`, `customer_feedback_and_complaints`, \n  `facility_management_issues`\nYour complete message should be a valid json string that can be read directly and only contain \nthe keys mentioned in the list above. Never enclose it in ```json...```, no newlines, no unnessacary whitespaces."
            }
        ],
        "response_format": {
            "type": "json_schema",
            "json_schema": {
                "name": "facility_output",
                "strict": true,
                "schema": {
                    "type": "object",
                    "properties": {
                        "urgency": {
                            "type": "string",
                            "description": "The urgency of the request",
                            "enum": [
                                "high",
                                "medium",
                                "low"
                            ]
                        },
                        "sentiment": {
                            "type": "string",
                            "description": "The sentiment of the request",
                            "enum": [
                                "positive",
                                "negative",
                                "neutral"
                            ]
                        },
                        "categories": {
                            "type": "object",
                            "properties": {
                                "emergency_repair_services": {
                                    "type": "boolean"
                                },
                                "routine_maintenance_requests": {
                                    "type": "boolean"
                                },
                                "quality_and_safety_concerns": {
                                    "type": "boolean"
                                },
                                "specialized_cleaning_services": {
                                    "type": "boolean"
                                },
                                "general_inquiries": {
                                    "type": "boolean"
                                },
                                "sustainability_and_environmental_practices": {
                                    "type": "boolean"
                                },
                                "training_and_support_requests": {
                                    "type": "boolean"
                                },
                                "cleaning_services_scheduling": {
                                    "type": "boolean"
                                },
                                "customer_feedback_and_complaints": {
                                    "type": "boolean"
                                },
                                "facility_management_issues": {
                                    "type": "boolean"
                                }
                            },
                            "required": [
                                "emergency_repair_services",
                                "routine_maintenance_requests",
                                "quality_and_safety_concerns",
                                "specialized_cleaning_services",
                                "general_inquiries",
                                "sustainability_and_environmental_practices",
                                "training_and_support_requests",
                                "cleaning_services_scheduling",
                                "customer_feedback_and_complaints",
                                "facility_management_issues"
                            ],
                            "additionalProperties": false
                        }
                    },
                    "required": [
                        "urgency",
                        "sentiment",
                        "categories"
                    ],
                    "additionalProperties": false
                }
            }
        },
        "additional_fields": {
            "modelParams": {
                "temperature": 0.7,
                "max_tokens": 100
            },
            "modelGroup": "chat"
        }
    }
}
```

