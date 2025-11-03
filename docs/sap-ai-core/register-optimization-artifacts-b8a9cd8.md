<!-- loiob8a9cd8f09be4863811ef98b67a38f3c -->

# Register Optimization Artifacts



<a name="loiob8a9cd8f09be4863811ef98b67a38f3c__prereq_i3k_vwn_s2c"/>

## Prerequisites

-   You've registered an object store for Amazon S3, OSS, or Azure Blob Storage. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-54068a9.md).
-   You've prepared a dataset in JSON format and stored it in your registered object store. For more information, see [Dataset preparation](dataset-preparation-b2625d7.md).



## Context

To run an optimization, you must provide a test dataset om JSON format. Your test dataset must contain data needed for the optimization, such as values for the prompt variables and ground truth references.

The following folder structure is recommended:

```
root-directory
└── testdata
    ├── dataset1.json
```

All optimization-relevant files must be stored under file paths relative to the URL of the registered artifact.



## Procedure

Send a request to the endpoint `$AI_API_URL/v2/lm/artifacts`, and include the prompt optimization label and the path to your artifact within your object store in your request.

> ### Sample Code:  
> ```
> curl --location --request POST "$AI_API_URL/v2/lm/artifacts" \
> --header "Authorization: Bearer $TOKEN" \
> --header 'Content-Type: application/json' \
> --header 'AI-Resource-Group: <resource group>' \
> --data-raw '{          
>         "name": "yourTestData",
>         "kind": "dataset",
>         "url": "ai://<name of object store secret>/<relative path to optimizations testData folder>"
>         "description": "demo artifacts for optimization flow.",
>         "scenarioId": "genai-optimizations"
>     }'
> ```

-   The `url` must begin with `ai://`, followed by the name of your object store secret and the relative path to the directory that contains your optimization files. The directory containing all files for optimization is registered as a single artifact.
-   The `scenarioId` must be `"genai-optimizations"`.

The data path specified in the URL field uses the name of the OSS you created as the path prefix. This replaces the originally assigned path prefix, as shown in the image below.

![](images/Data_Path_for_Evaluation_Artifacts_de48b42.png)



<a name="loiob8a9cd8f09be4863811ef98b67a38f3c__postreq_azv_4dq_1fc"/>

## Next Steps

Create a configuration for your optimization. For more information, see [Create a Configuration for an Optimization](create-a-configuration-for-an-optimization-40ba168.md).

