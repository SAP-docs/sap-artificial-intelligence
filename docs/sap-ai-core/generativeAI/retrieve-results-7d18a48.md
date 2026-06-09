<!-- loio7d18a48d2b424e209ac88ee922ab3410 -->

# Retrieve Results



## Prerequisites

-   You've created a batch job. For more information, see [Create a Batch Job](create-a-batch-job-bb19774.md).
-   The status of your batch job is `COMPLETED`. For more information, see [Check Batch Status](check-batch-status-32536ef.md).



## Context

The batch service writes output to a subdirectory named after the batch ID, under the output URI specified at job creation.

> ### Example:  
> If the output URI was `ai://my-object-store/output/`, the results are written to:
> 
> ```
> ai://my-object-store/output/<batch_id>/output.jsonl
> 
> ```

> ### Example:  
> If any individual requests failed during processing, an error file is written alongside the output file:
> 
> ```
> ai://my-object-store/output/<batch_id>/error.jsonl
> 
> ```



## Output File Format

Each line in the output file corresponds to one request from the input file, matched by `custom_id`:

```
{"id": "batch-response-1", "custom_id": "request-1", "response": {"status_code": 200, "body": {"id": "chatcmpl-123", "choices": [{"message": {"content": "Machine learning is a subfield of..."}}]}}}
{"id": "batch-response-2", "custom_id": "request-2", "response": {"status_code": 200, "body": {"id": "chatcmpl-124", "choices": [{"message": {"content": "Neural networks are computational models..."}}]}}}

```

> ### Note:  
> The status `COMPLETED` indicates that the batch as a whole was processed. Individual requests within the batch may still have failed. Check `response.status_code` for each entry in the output file, and review the error file for failed requests.

