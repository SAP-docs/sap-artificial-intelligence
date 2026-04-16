<!-- loio54068a9621e5490fb45b4f794aef181e -->

# Register an Object Store for Optimizations



<a name="loio54068a9621e5490fb45b4f794aef181e__context_ddj_r3f_52c"/>

## Context

> ### Restriction:  
> You must create an **object store secret** named **default** to store optimization output artifacts.
> 
> For**input artifacts** only, you may create multiple object store secrets with different names as needed.



## Procedure

To create an object store secret for your object store, send a POST request to the endpoint `$AI_API_URL/v2/admin/objectStoreSecrets` and include your credentials in the body of your request.

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

-   For Azure Blob Storage:

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


> ### Tip:  
> The `pathPrefix` is useful if you share the same bucket for different projects. You can set the name of your project folder to `my-ml-project1`, for example. All data is then stored in that folder.

> ### Note:  
> If the `AI-Resource-Group` header isn't specified, the *<Resource Group\>* is assigned the value `"default"` automatically.

