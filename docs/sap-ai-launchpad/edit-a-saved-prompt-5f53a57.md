<!-- loio5f53a57b2beb4eac846201ecb4daae21 -->

# Edit a Saved Prompt



<a name="loio5f53a57b2beb4eac846201ecb4daae21__prereq_yxf_gyb_rzb"/>

## Prerequisites

-   You’ve selected the AI API connection and resource group that you used in the activation steps.

-   You have either the `genai_manager` or `prompt_manager` role, or you are assigned a role collection that contains one of these roles. For more information, see [Roles and Authorizations](security-e4cf710.md#loio4ef8499d7a4945ec854e3b4590830bcc).


> ### Note:  
> Prompts are saved in one region only and can only be retrieved or deleted by an instance of AI launchpad in that region.



<a name="loio5f53a57b2beb4eac846201ecb4daae21__steps_tfy_jcv_jzb"/>

## Procedure

1.  Navigate to your desired prompt. For more information, see [View a Saved Prompt](view-a-saved-prompt-d07a272.md).

2.  Choose the entry for the version you want to edit.

3.  Choose *Open in Editor*. Make your changes.

    ![](images/eidutsavedprompt2503b_69091b3.png)

    > ### Note:  
    > If the model used for your prompt is no longer available you will be notified when you open the prompt in the editor and you must choose another model.

    ![](images/choose_new_model_e70d769.png)

    For changes to the prompt message, the *Save* button is available, and saving creates a new prompt version.

    For changes to meta data only, the *Update* button is available, and updating the meta data for the same prompt version.

    Meta data updates at prompt level, such as *Prompt Name* and *Collection* are updated across all versions of the prompt

    Meta data updates at prompt version level, such as *Tags* and *Notes* are updated across the current version of the prompt




## Next Steps

You can run your prompt again, making changes to the prompt message, parameters or model selection to change the outcome. For more information, see [Prompt Experimentation](prompt-experimentation-384cc0c.md).

