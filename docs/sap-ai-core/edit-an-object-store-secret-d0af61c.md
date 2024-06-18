<!-- loiod0af61cc34194ebabd7b9cf651404307 -->

# Edit an Object Store Secret



<a name="loiod0af61cc34194ebabd7b9cf651404307__section_a2q_fps_vnb"/>

## Using Postman

1.  Send a PATCH request to the endpoint

    `{{apiurl}}/v2/admin/objectStoreSecrets/{{objectStoreName}}`

    .

2.  As the request body, select the *raw* radio button and enter your object store secret details.

    > ### Note:  
    > For all storage types **except** Azure Blob Storage, all *<data\>* fields are required. For Azure, required fields are specified.

    -   For Amazon S3:

        ```json
        {
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
                "ENDPOINT": "oss-cn-shanghai.aliyuncs.com",
                "REGION": "",
                "ACCESS_KEY_ID": "xxxxx",
                "SECRET_ACCESS_KEY": "xxxxx"
            }
        }
        
        ```

    -   For SAP HANA Cloud, Data Lake:

        ```json
        {
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




<a name="loiod0af61cc34194ebabd7b9cf651404307__section_phb_4hr_yqb"/>

## Using curl

1.  Register your object store secret details using the endpoint `$AI_API_URL/v2/admin/objectStoreSecrets/{{objectStoreName}}`.

    > ### Note:  
    > For all storage types **except** Azure Blob Storage, all *<data\>* fields are required. For Azure, required fields are specified.

    -   For Amazon S3:

        ```
        curl --location --request PATCH "$AI_API_URL/v2/admin/objectStoreSecrets/{{objectStoreName}}" \
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
        curl --location --request PATCH "$AI_API_URL/v2/admin/objectStoreSecrets/{{objectStoreName}}" \
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
        curl --location --request PATCH "$AI_API_URL/v2/admin/objectStoreSecrets/{{objectStoreName}}" \
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

        ```json
        curl --location --request PATCH "$AI_API_URL/v2/admin/objectStoreSecrets/{{objectStoreName}}" \
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
> The `pathPrefix` is useful if you share the same bucket for different projects. You can set the name of your project folder to `my-ml-project1`, for example. All data will then be stored in that folder.

> ### Note:  
> If the `AI-Resource-Group` header is not specified, the *<Resource Group\>* is assigned the value `"default"` automatically.

