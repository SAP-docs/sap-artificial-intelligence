<!-- loiob2625d72bc644233b80f148846cc04b2 -->

# Dataset preparation

The dataset shows the desirable outcome of an input prompt and corresponding values for placeholders in the input prompt.

Your dataset must meet the following conditions:

-   It has a minimum of 25 and maximum of 200 samples

-   It contains the exact placeholder names that are used in the template in the “fields” object.


> ### Caution:  
> Do not include confidential of personally identifiable information in the dataset.

For example:

> ### Sample Code:  
> ```
> [
>     {
>         "fields": {
>             "input": "Subject: Urgent Assistance Required for Specialized Cleaning Services\n\nDear ProCare 
> 			Facility Solutions Support Team. Could you please arrange for a specialized cleaning team to 
> 			visit our home at the earliest convenience? We would greatly appreciate it if this could be 
> 			prioritized since we want to host a large party this week.\n\nThank you for your prompt 
> 			attention to this matter. We look forward to your swift response and assistance.\n\nBest 
> 			regards,\n[Sender]"
>         },
>         "answer": "{\"categories\": {\"routine_maintenance_requests\": false, 
> 		\"customer_feedback_and_complaints\": false, \"training_and_support_requests\": false, 
> 		\"quality_and_safety_concerns\": false, \"sustainability_and_environmental_practices\": false, 
> 		\"cleaning_services_scheduling\": false, \"specialized_cleaning_services\": true, 
> 		\"emergency_repair_services\": false, \"facility_management_issues\": false, 
> 		\"general_inquiries\": false}, \"sentiment\": \"neutral\", \"urgency\": \"high\"}"
>     },
>   {...}
> ]
> ```

