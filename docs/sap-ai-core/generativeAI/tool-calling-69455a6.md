<!-- loio69455a6a2b9c484fb02c73b716b211df -->

# Tool Calling

You can define a tools for the model to call to perform specific tasks. To do this, include a `tools` field in your prompt template and populating it with details of your tool. `tools` is an optional field. Tools will only be called if the model finds them relevant to answer the prompt.

For example:

> ### Sample Code:  
> ```
> {
>     "name": "tools-prompt-template",
>     "version": "0.0.1",
>     "scenario": "genai-optimizations",
>     "spec": {
>         "template": [
>             {
>                 "role": "system",
>                 "content": "you are a helpful assistant"
>             },
>             {
>                 "role": "user",
>                 "content": "{{?question}}"
>             }
>         ],
>         "tools": [
>             {
>                 "type": "function",
>                 "function": {
>                     "name": "calculate_distance",
>                     "description": "Calculate the distance between two locations.",
>                     "strict": true,
>                     "parameters": {
>                         "type": "object",
>                         "properties": {
>                             "origin": {
>                                 "type": "string",
>                                 "description": "The starting location (city or address)."
>                             },
>                             "destination": {
>                                 "type": "string",
>                                 "description": "The ending location (city or address)."
>                             },
>                             "unit": {
>                                 "type": "string",
>                                 "description": "Distance unit. Options: 'km', 'miles'. Default 'km'."
>                             }
>                         },
>                         "required": [
>                             "origin",
>                             "destination",
>                             "unit"
>                         ],
>                         "additionalProperties": false
>                     }
>                 }
>             },
>             {
>                 "type": "function",
>                 "function": {
>                     "name": "restaurant_search",
>                     "description": "Find restaurants matching specific criteria in a given location.",
>                     "strict": true,
>                     "parameters": {
>                         "type": "object",
>                         "properties": {
>                             "location": {
>                                 "type": "string",
>                                 "description": "The city or area to search in."
>                             },
>                             "cuisine": {
>                                 "type": "string",
>                                 "description": "The type of cuisine, e.g. 'Italian', 'Chinese', 'Mexican'."
>                             },
>                             "price_range": {
>                                 "type": "string",
>                                 "description": "Price tier. Options: 'budget', 'moderate', 'fine_dining'. Default 'moderate'."
>                             },
>                             "min_rating": {
>                                 "type": "number",
>                                 "description": "Minimum star rating (0.0-5.0). Default 0.0."
>                             }
>                         },
>                         "required": [
>                             "location",
>                             "cuisine",
>                             "price_range",
>                             "min_rating"
>                         ],
>                         "additionalProperties": false
>                     }
>                 }
>             },
>             {
>                 "type": "function",
>                 "function": {
>                     "name": "weather_forecast",
>                     "description": "Get the weather forecast for a location over a specified number of days.",
>                     "parameters": {
>                         "type": "dict",
>                         "properties": {
>                             "location": {
>                                 "type": "string",
>                                 "description": "The city to get the forecast for."
>                             },
>                             "days": {
>                                 "type": "integer",
>                                 "description": "Number of days to forecast (1-14)."
>                             },
>                             "units": {
>                                 "type": "string",
>                                 "description": "Temperature units. Options: 'celsius', 'fahrenheit'. Default 'celsius'."
>                             }
>                         },
>                         "required": [
>                             "location",
>                             "days",
>                             "units"
>                         ],
>                         "additionalProperties": false
>                     }
>                 }
>             },
>             {
>                 "type": "function",
>                 "function": {
>                     "name": "currency_conversion",
>                     "description": "Convert an amount from one currency to another using current exchange rates.",
>                     "parameters": {
>                         "type": "object",
>                         "properties": {
>                             "amount": {
>                                 "type": "number",
>                                 "description": "The amount of money to convert."
>                             },
>                             "from_currency": {
>                                 "type": "string",
>                                 "description": "The source currency code, e.g. 'USD', 'EUR', 'GBP'."
>                             },
>                             "to_currency": {
>                                 "type": "string",
>                                 "description": "The target currency code, e.g. 'USD', 'EUR', 'GBP'."
>                             }
>                         },
>                         "required": [
>                             "amount",
>                             "from_currency",
>                             "to_currency"
>                         ],
>                         "additionalProperties": false
>                     }
>                 }
>             },
>             {
>                 "type": "function",
>                 "function": {
>                     "name": "grocery_store",
>                     "description": "Find nearby grocery stores or check product availability and pricing.",
>                     "parameters": {
>                         "type": "object",
>                         "properties": {
>                             "location": {
>                                 "type": "string",
>                                 "description": "The city or area to search in."
>                             },
>                             "product": {
>                                 "type": "string",
>                                 "description": "A specific product to check availability for."
>                             },
>                             "organic_only": {
>                                 "type": "boolean",
>                                 "description": "Whether to filter for organic products only. Default false."
>                             }
>                         },
>                         "required": [
>                             "location",
>                             "product",
>                             "organic_only"
>                         ],
>                         "additionalProperties": false
>                     }
>                 }
>             }
>         ],
>         "additional_fields": {
>             "modelParams": {
>                 "temperature": 0.7,
>                 "max_tokens": 100
>             },
>             "modelGroup": "chat"
>         }
>     }
> }
> ```

