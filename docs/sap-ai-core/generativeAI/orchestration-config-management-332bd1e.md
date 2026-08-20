<!-- loio332bd1ed3bb040cca58e17b3b9ca1702 -->

# Orchestration Config Management

Manage the lifecycle of your orchestration configurations, from design to runtime.

You can store, version, and manage orchestration configs as reusable assets in the prompt registry. This makes them discoverable across your applications and orchestration workflows, enabling better governance and reusability.

Orchestration configs can reference existing prompt templates by ID or by name, scenario, and version, allowing you to build reusable orchestration workflows that leverage your prompt template library.

Stored orchestration configs can be referenced in LLM Orchestration completion requests, providing an alternative to inline configuration definitions.

The Prompt Registry consists of the following interfaces for orchestration configs:

-   The imperative API supports full CRUD operations and is recommended for refining orchestration configs in design-time use cases. Iterations are tracked and can be viewed in the history endpoint. For more information, see [Create an Orchestration Config \(Imperative\)](create-an-orchestration-config-imperative-2f27317.md).

-   The declarative API utilizes SAP AI Core applications and is recommended for runtime application use cases and CI/CD pipelines. You can manage your orchestration configs in a git repository declaratively. Your commits are automatically synchronized with the Prompt Registry For more information, see [Create an Orchestration Config \(Imperative\)](create-an-orchestration-config-imperative-2f27317.md).


The interfaces can all be consumed either directly via the API or through Orchestration.

Stored orchestration configs reduce the complexity of managing orchestration configurations by providing lifecycle management capabilities including versioning, history tracking, and import and export functionality.

The orchestration config endpoints are imperative API operations that support full CRUD functionality for both design-time and runtime use cases. Iterations are tracked and can be viewed in the history endpoint.

> ### Note:  
> Orchestration configs are only available through the imperative API and are managed at the tenant level.

-   **[Create an Orchestration Config \(Imperative\)](create-an-orchestration-config-imperative-2f27317.md "")**  

-   **[Create an Orchestration Config \(Declarative\)](create-an-orchestration-config-declarative-508e66f.md "")**  

-   **[Get Orchestration Configs](get-orchestration-configs-e8310f5.md "")**  

-   **[Get Orchestration Config History](get-orchestration-config-history-743e913.md "")**  

-   **[Use an Orchestration Config in LLM Orchestration](use-an-orchestration-config-in-llm-orchestration-97e4cd2.md "")**  

-   **[Export an Orchestration Config](export-an-orchestration-config-44db4a5.md "")**  

-   **[Import an Orchestration Config](import-an-orchestration-config-2b9affa.md "")**  

-   **[Delete an Orchestration Config](delete-an-orchestration-config-d843b44.md "")**  


