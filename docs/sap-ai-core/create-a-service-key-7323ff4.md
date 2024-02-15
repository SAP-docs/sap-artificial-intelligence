<!-- loio7323ff4e37ba41c198b06e9669b80920 -->

# Create a Service Key



## Procedure

1.  On the *Instances and Subscriptions* page, find your new instance and choose *Create Service Key* from the dropdown.

    ![](images/View_Service_Instances_7ff0ecc.png)

2.  Enter a name for your service key and click *Create*.

    ![](images/New_Service_Key_0019ba4.png)



3.  Download your service key to save it.




<a name="loio7323ff4e37ba41c198b06e9669b80920__result_wml_znv_p4b"/>

## Results

You now have your service key, which provides URLs and credentials for accessing the SAP AI Core instance through SAP AI Launchpad, SAP AI Core toolkit Postman, or curl.

![](images/Service_Key_Credentials_1e1342e.png)

Your key will include:

-   `clientid`, `clientsecret`, and `url` can be used to generate your authentication token.

-   `identityzone` and `identityzoneid` represent your tenant ID.

-   `appname` provides the service instance details if service instance isolation is implemented.

-   `serviceurls` allow you to interact with SAP AI Core once your authentication token has been generated.

    -   `AI_API_URL`: Unified AI API to handle ML artifacts \(such as training, data, models, and deployments\) across multiple hyperscalers.



