<!-- loio50a6d9f4440c4a06b53b0f17017bdba8 -->

# Onboarding

To onboard a service, complete the following:

1.  Create a brokerSecret to be used as credentials when registering the service broker.
    1.  Use a new POST request to URL `{{apiurl}}/v2/admin/secrets`
    2.  Provide credentials \(base64 encoded\) in the request body in JSON format:

        ```
        {
        "name": "broker-credentials",
        "data": {
        		"username": "bXktc2VjcmV0LWNyZWRlbnRpYWw=",
        		"password": "bXktc2VjcmV0LW90aGVyLWNyZWRlbnRpYWw="
        		}
        }
        ```

    3.  Specify the scope of the request in the header: AI-Tenant-Scope: true
    4.  Send the request.

2.  Modify the brokerSecret specification section using these details:

    ```
    
    apiVersion: ai.sap.com/v1alpha1
    kind: Service
    metadata:
    	name: sample-service
    spec:	
    	brokerSecret:
    		name: broker-credentials
    		usernameKeyRef: username
    		passwordKeyRef: password
    	description: Service used for demos
    	capabilities:
    		basic:
    			staticDeployments: true
    			userDeployments: true
    			createExecutions: true
    		logs:
    			executions: true
    			deployments: true
    	serviceCatalog:
    		- extendCredentials:
    			shared:
    				serviceUrls:
    					AI_SVC_URL: https://api.ai.internalprod.eu-central-1.aws.ml.hana.ondemand.com
    		extendCatalog:
    
    			name: sample-service
    			id: sample-service-broker-id
    			description: sample service
    			bindable: true
    			plans:
    				- id: sample-service-standard
    				description: Standard plan for sample Service
    				name: standard
    				free: false
    				metadata:
    					supportedPlatforms:
    						- cloudfoundry
    						- kubernetes
    						- sapbtp
    
    ```

    > ### Note:  
    > The username and password are key names from the broker credentials in the previous step.

3.  Update the spec.serviceCatalog\[\].extendCredentials with the service URL you want to provide to the consumer, which will be part of the service key. Provide catalog details under spec.serviceCatalog\[\].extendCatalog.
4.  Push your service custom resource to your registered GitHub repository, and wait for the sync to be successful.
5.  Once it has synced, Check the service details by sending a GET request to URL `{{apiurl}}/v2/admin/services`.

    ```
    
    {
    	"count": 1
    	"resources": [
    		{
    		"name": "sample-service",
    		"description": "Service used for demos",
    		"status": "PROVISIONED",
    		"url": "https://aif-xyzabc.servicebroker.internalprod.eu-central.aws.ml.hana.ondemand.com"
    		}
    	]
    }
    
    ```

    Take note of the service broker URL.

6.  Register the service broker using smctl as subaccount-scoped.
    1.  Test the registration of the service broker first as subaccount-scoped, before you register it globally. Subaccount-scoped means that your service is automatically visible in the catalog of environments where it's registered. You can follow steps described in Service Manager Guide to [set up for smctl](https://wiki.wdf.sap.corp/wiki/display/CPC15N/Test).

        Once smctl is installed, login as shown:

        ```
        
        # env variables
        SERVICE_MANAGER_URL=<sm url e.g. https://service-manager.cfapps.sap.hana.ondemand.com/>
        SVC_SUBACCOUNT_USER=<user-with-servicemanager-role>SVC_SUBACCOUNT_PWD=<password + 2FA>
        SERVICE_BROKER_URL=https://aif-xyzabc.servicebroker.internalprod.eu-central.aws.ml.hana.ondemand.com
        SVC_SUBACCOUNT_SUBDOMAIN=<subaccount e.g. subaccountxyz>
        SERVICE_BROKER_USER=<broker username provided in secret>
        SERVICE_BROKER_PWD=<broker password provided in secret>
        
        # smctl login
        smctl login -a $SERVICE_MANAGER_URL \
        	--param subdomain=$SVC_SUBACCOUNT_SUBDOMAIN \
        	-u=$SVC_SUBACCOUNT_USER \
        	-p=$SVC_SUBACCOUNT_PWD
        ```

    2.  Register your service-broker by providing the broker-name, URL, and credentials.

        ```
        
        # register service-broker
        smctl register-broker sample-service $SERVICE_BROKER_URL -b $SERVICE_BROKER_USER:$SERVICE_BROKER_PWD
        
        # service-broker registration should complete successfully
        
        ```

        With the service-broker registered successfully, the service is available in the *Service Marketplace*.

        ```
        
        # assuming you are logged in to Cloud
                                        Foundry, provided correct subaccount, get service plan information
        
        cf marketplace -s sample-service
        ```



Consumers can now create a service instance and service-key. On creation of service instance, SAP AI Core will create a corresponding resource-group with id = instance id, and the service is now ready for use.

