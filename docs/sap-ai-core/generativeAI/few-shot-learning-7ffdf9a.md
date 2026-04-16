<!-- loio7ffdf9a6d89c465d8058634e7c4bb19c -->

# Few-Shot Learning



<a name="loio7ffdf9a6d89c465d8058634e7c4bb19c__section_vr2_rpj_12c"/>

## Prerequisites

You have a running orchestration deployment and have retrieved your orchestration deployment URL. For more information, see [Get An Orchestration Deployment URL](get-an-orchestration-deployment-url-ec7c703.md) and [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).



<a name="loio7ffdf9a6d89c465d8058634e7c4bb19c__section_kdz_tqj_12c"/>

## Process

The following example shows how you can configure the templating module to use a few-shot learning prompt.

```
curl --request POST $ORCH_DEPLOYMENT_URL/v2/completion \
    --header 'content-type: application/json' \
    --header "Authorization: Bearer $TOKEN" \
    --header "AI-Resource-Group: $RESOURCE_GROUP" \
    --data-raw '{
    "config": {
      "modules": {
        "prompt_templating": {
          "prompt": {
                "template": [
                  {
                    "role": "system",
                    "content": "You classify input text into the two following categories: Business, Economics, Tech, and other"
                  },
                  {
                    "role": "user",
                    "content": "input text: `Comcast launches prepaid plans`"
                  },
                  {
                    "role": "assistant",
                    "content": "Business"
                  },
                  {
                    "role": "user",
                    "content": "input text: `Slower Fed Pivot Weakens Rate-Cut Bets Across Emerging Asia`"
                  },
                  {
                    "role": "assistant",
                    "content": "Economics"
                  },
                  {
                    "role": "user",
                    "content": "input text: {{?input}}"
                  }
              ]
          },
          "model": {
            "name": "gpt-4o",
            "params": {
              "max_completion_tokens": 300,
              "temperature": 2
            }
         }
        }
      }
    },
    "placeholder_values": {
        "input": "Scaling up neural models has yielded significant advancements in a wide array of tasks, particularly in language generation."

    }
}
 '
```

In this case, the template contains an array of messages, including a system message, as well as several user and assistant messages. The actual input to categories is configured with the final user message and the content `input text: {{?input}}`. The input parameter input is set to `Scaling up neural models has yielded significant advancements in a wide array of tasks, particularly in language generation.`.

**Related Information**  


[Leveraging Orchestration Capabilities to Enhance Responses](https://developers.sap.com/tutorials/ai-core-orchestration-consumption-opt.html)

[Libraries and SDKs](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/499309d6e371419fb7a88b7d68c20a31.html "Explore additional SDKs and libraries that you can use with SAP AI Core.") :arrow_upper_right:

