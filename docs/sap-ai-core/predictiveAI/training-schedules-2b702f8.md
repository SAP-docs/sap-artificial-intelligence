<!-- loio2b702f8b3d0746f685ac4eea4eeb1755 -->

# Training Schedules

In order to run executions periodically, you can define a schedule to start your executions automatically. To do this, you must have prepared your configuration for the execution.

Training schedules have a start and end timestamp. The start timestamp defines when the schedule will first be run to generate executions. The end timestamp defines when the schedule will expire.

A schedule that has not yet expired has ACTIVE status. Upon expiry, the status will changed to INACTIVE, and no further executions will start.

The format for these timestamps is defined by RFC3339 section 5.6, without fractions of seconds, for example: `2023-02-09T12:53:47Z`. All timestamps are interpreted in UTC time. For more information, see [RFC3339 section 5.6](https://www.rfc-editor.org/rfc/rfc3339#section-5.6)and [AI API Overview](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/716d4c38e3054c93a9d481b51cc66298.html "The AI API lets you manage your AI assets (such as training scripts, data, models, and model servers) across multiple runtimes.") :arrow_upper_right:.

-   **[Create a Training Schedule](create-a-training-schedule-bd409a9.md "")**  

-   **[List Executions Created by a Training Schedule](list-executions-created-by-a-training-schedule-2c1ecfb.md "")**  

-   **[Stop or Resume a Schedule](stop-or-resume-a-schedule-d6ab976.md "")**  

-   **[Change an Existing Training Schedule](change-an-existing-training-schedule-18caf4b.md "")**  

-   **[Delete a Training Schedule](delete-a-training-schedule-9dc25e1.md "")**  


