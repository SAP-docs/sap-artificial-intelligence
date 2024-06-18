<!-- loiob083d73f672c428faac3048b74733546 -->

# Register an Object Store Secret

Connect SAP AI Core to a cloud object store and manage access using an object store secret. The connected storage stores your dataset, models, and other cache files of the Metaflow Library for SAP AI Core.

Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.



<a name="loiob083d73f672c428faac3048b74733546__section_t3r_qmc_gyb"/>

## Prerequisites

You have completed the Initial Setup. For more information, see [Initial Setup](initial-setup-38c4599.md).



<a name="loiob083d73f672c428faac3048b74733546__section_spp_3c3_dxb"/>

## Context

SAP AI Core supports multiple hyperscaler object stores, such as Amazon S3, OSS \(Alicloud Object Storage Service\), SAP HANA Cloud, Data Lake, and Azure Blob Storage.



<a name="loiob083d73f672c428faac3048b74733546__section_a2q_fps_vnb"/>

## Using Postman

1.  Send a POST request to the endpoint `{{apiurl}}/v2/admin/objectStoreSecrets`.
2.  As the request body, select the *raw* radio button and enter your object store secret details.

    > ### Note:  
    > For all storage types **except** Azure Blob Storage, all *<data\>* fields are required. For Azure, required fields are specified.

    -   For Amazon S3:

        ```json
        {
        	"name": "<Your identifier>",
        	"data": {
        		"AWS_ACCESS_KEY_ID": "<AWS access key ID>",
        		"AWS_SECRET_ACCESS_KEY": "<AWS secret access key>"
        	},
        	"type": "S3",
        	"bucket": "<S3 bucket name>",
        	"endpoint": "<S3 end point>",
        	"region": "<S3 region>",
        	"pathPrefix": "<A path prefix that follows the bucket name>"
        }
        
        
        ```

    -   For OSS \(Alicloud Object Storage Service\):

        ```json
        {
            "name": "default",
            "type": "oss",
            "pathPrefix": "<path prefix to be appended with bucketname>",
            "data": {
                "BUCKET": "<bucket-name>",
                "ENDPOINT": "oss-cn-shanghai.aliyuncs.com",{
            "name": "default",
            "type": "S3",
            "bucket": "{
            "name": "default",
            "type": "oss",
            "pathPrefix": "<path prefix to be appended with bucketname>",
            "data": {
                "REGION": "",
                "ACCESS_KEY_ID": "xxxxx",
                "SECRET_ACCESS_KEY": "xxxxx"
            }
        }
        
        ```

    -   For SAP HANA Cloud, Data Lake:

        ```json
        
                "BUCKET": "{
          "name": "default",
          "type": "webhdfs",
          "pathPrefix": "<path prefix to be appended>",
          "data": {
            // e.g. https://c32727c8-4260-4c37-b97f-ede322dcfa8f.files.hdl.canary-eu10.hanacloud.ondemand.com
            "HDFS_NAMENODE": "https://<file-container-name>.files.hdl.canary-eu10.hanacloud.ondemand.com",
            "TLS_CERT": "-----BEGIN CERTIFICATE-----\nMIICmjCCAYIxxxxxxxxxxxxR4wtC32bGO66D+Jc8RhaIA==\n-----END CERTIFICATE-----\n",
            "TLS_KEY": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqxxxxxxxxxxxxnor+rtZHhhzEfX5dYLCS5Pww=\n-----END PRIVATE KEY-----\n",
            "HEADERS": "{\"x-sap-filecontainer\": \"<file-container-name>\", \"Content-Type\": \"application/octet-stream\"}"
          }
        }
        ```

    -   For Azure Blob Storage:

        > ### Restriction:  
        > For **executions** only, access keys are supported. SAS tokens are **not** supported.
        > 
        > For **deployments**, access keys and SAS tokens are supported.

        ```json
        {
        	"name": "default",
        	"type": "azure",
        	"pathPrefix": "<path prefix to be appended>",
        	"data": {
        		"CONTAINER_URI": "https://account_name.blob.core.windows.net/container_name",  //required
        		"REGION": "<region name>",                  //optional
        		"CLIENT_ID": "<azure client id>",           //optional
        		"CLIENT_SECRET": "<azure client secret>",   //optional
        		"STORAGE_ACCESS_KEY": "sas_token",          //required
        		"TENANT_ID": "azure tenant id",             //optional
        		"SUBSCRIPTION_ID": "subscription id",       //optional
        	}
        }
        ```


3.  Send the request.

    The following shows a request using S3.

    ![](images/POST_create_objectstoresecret_4548dd0.png)




<a name="loiob083d73f672c428faac3048b74733546__section_phb_4hr_yqb"/>

## Using curl

1.  Register your object store secret details using the endpoint `/v2/admin/objectStoreSecrets`.

    > ### Note:  
    > For all storage types **except** Azure Blob Storage, all *<data\>* fields are required. For Azure, required fields are specified.

    -   For Amazon S3:

        ```
        curl --location --request POST "$AI_API_URL/v2/admin/objectStoreSecrets" \
        --header "Authorization: Bearer $TOKEN" \
        --header 'Content-Type: application/json' \
        --header 'AI-Resource-Group: <Resource group>' \
        --data-raw '{
                "name": "default",
                "type": "S3",
                "bucket": "<S3 bucket name>",
                "endpoint": "<S3 end point>",
                "pathPrefix": "<A path prefix that follows the bucket name>",
                "region": "<S3 region>",
                "data": {
                      "AWS_ACCESS_KEY_ID": "<AWS access key ID>",
                      "AWS_SECRET_ACCESS_KEY": "<AWS secret access key>"
                }
            }'
        
        ```

    -   For OSS \(Alicloud Object Storage Service\):

        ```json
        curl --location --request POST "$AI_API_URL/v2/admin/objectStoreSecrets" \
        --header "Authorization: Bearer $TOKEN" \
        --header 'Content-Type: application/json' \
        --header 'AI-Resource-Group: <Resource group>' \
        --data-raw '{
            	"name": "default",
            	"type": "oss",
            	"pathPrefix": "<path prefix to be appended with bucketname>",
            	"data": {
           	     "BUCKET": "<bucket-name>",
           	     "ENDPOINT": "oss-cn-shanghai.aliyuncs.com",
           	     "REGION": "",
           	     "ACCESS_KEY_ID": "xxxxx",
           	     "SECRET_ACCESS_KEY": "xxxxx"
           	 }
        }
        
        ```

    -   For SAP HANA Cloud, Data Lake:

        ```json
        curl --location --request POST "$AI_API_URL/v2/admin/objectStoreSecrets" \
        --header "Authorization: Bearer $TOKEN" \
        --header 'Content-Type: application/json' \
        --header 'AI-Resource-Group: <Resource group>' \
        --data-raw '{
          	"name": "default",
          	"type": "webhdfs",
          	"pathPrefix": "<path prefix to be appended>",
         	 "data": {
        	    // e.g. https://c32727c8-4260-4c37-b97f-ede322dcfa8f.files.hdl.canary-eu10.hanacloud.ondemand.com
        	    "HDFS_NAMENODE": "https://<file-container-name>.files.hdl.canary-eu10.hanacloud.ondemand.com",
        	    "TLS_CERT": "-----BEGIN CERTIFICATE-----\nMIICmjCCAYIxxxxxxxxxxxxR4wtC32bGO66D+Jc8RhaIA==\n-----END CERTIFICATE-----\n",
        	    "TLS_KEY": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqxxxxxxxxxxxxnor+rtZHhhzEfX5dYLCS5Pww=\n-----END PRIVATE KEY-----\n",
        	    "HEADERS": "{\"x-sap-filecontainer\": \"<file-container-name>\", \"Content-Type\": \"application/octet-stream\"}"
        	  }
        }
        ```

    -   For Azure Blob Storage:

        > ### Restriction:  
        > For **executions** only, access keys are supported. SAS tokens are **not** supported.
        > 
        > For **deployments**, access keys and SAS tokens are supported.

        ```json
        curl --location --request POST "$AI_API_URL/v2/admin/objectStoreSecrets" \
        --header "Authorization: Bearer $TOKEN" \
        --header 'Content-Type: application/json' \
        --header 'AI-Resource-Group: <Resource group>' \
        --data-raw '{
        		"name": "default",
        		"type": "azure",
        		"pathPrefix": "<path prefix to be appended>",
        		"data": {
        			"CONTAINER_URI": "https://account_name.blob.core.windows.net/container_name",  //required
        			"REGION": "<region name>",                  //optional
        			"CLIENT_ID": "<azure client id>",           //optional
        			"CLIENT_SECRET": "<azure client secret>",   //optional
        			"STORAGE_ACCESS_KEY": "sas_token",          //required
        			"TENANT_ID": "azure tenant id",             //optional
        			"SUBSCRIPTION_ID": "subscription id",       //optional
        	}
        }
        ```





> ### Note:  
> For input artifacts only
> 
> You can create multiple secrets using different values for `name`, but you must create a default first.

> ### Tip:  
> The `pathPrefix` is useful if you share the same bucket for different projects. You can set the name of your project folder to `my-ml-project1`, for example. All data is then stored in that folder.

> ### Note:  
> If the `AI-Resource-Group` header is not specified, the *<Resource Group\>* is assigned the value `"default"` automatically.

> ### Restriction:  
> When using an SAP HANA Data Lake object store with output artifacts pointing to a directory, you cannot use `archive: none: {}` in your workflow templates to disable artifact archiving. For more information, see [Workflow Templates](workflow-templates-83523ab.md).

