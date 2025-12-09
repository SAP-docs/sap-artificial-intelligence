<!-- loio19412e09b6374287bed706112a56bcc1 -->

# Register Evaluation Artifacts

You can evaluate different orchestration configurations and prompt variable values against the shortlisted models to find the best orchestration configuration for your use case.



<a name="loio19412e09b6374287bed706112a56bcc1__prereq_i3k_vwn_s2c"/>

## Prerequisites

-   You have an orchestration deployment running. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md) or [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).
-   You've registered an object store for Amazon S3, OSS, or Azure Blob Storage. For more information, see [Register an Object Store for Optimizations](register-an-object-store-for-optimizations-54068a9.md).



## Context

To run an evaluation, you must provide the following artifacts:

-   A test dataset containing data needed for the evaluation, such as values for the prompt variables and ground truth references. The following file formats are supported:
    -   `CSV`
    -   `JSON`
    -   `JSONL`


The following folder structure is recommended:

```
root-directory
└── testdata
    ├── dataset1.jsonl
    └── dataset2.csv
```



## Procedure

Send a request to the endpoint `{{apiurl}}/v2/lm/artifacts`, and include the prompt evaluation label and the path to your artifact within your object store in your request.

> ### Sample Code:  
> ```
> curl --location --request POST "{{apiurl}}/v2/lm/artifacts" \
> --header "Authorization: Bearer $TOKEN" \
> --header 'Content-Type: application/json' \
> --header 'AI-Resource-Group: <resource group>' \
> --data-raw '{          
>         "name": "yourTestData",
>         "kind": "other",
>         "url": "ai://<name of object store secret>/<relative path to evaluations testData folder>"
>         "description": "demo artifacts for evaluation flow.",
>         "scenarioId": "genai-evaluations"
>     }'
> ```

-   The `url` must begin with `ai://`, followed by the name of your object store secret and the relative path to the directory that contains your evaluation files. The directory containing all files for evaluation is registered as a single artifact.
-   The `scenarioId` must be `"genai-evaluations"`.

The data path specified in the URL field uses the name of the OSS you created as the path prefix. This replaces the originally assigned path prefix, as shown in the image below.

![Diagram showing extraction of a path prefix](images/Data_Path_for_Evaluation_Artifacts_de48b42.png)

