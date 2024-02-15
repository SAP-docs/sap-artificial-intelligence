<!-- loio869b2b16c76b488e8fdbbff20522f63d -->

# Configuration Data and Secrets

Workloads can access network resources other than object stores by using credentials at runtime. The ways of including this information at runtime have different standards when it comes to confidentiality.

-   For **sensitive** information:

    SAP AI Core allows you to include secrets in the form of generic secrets. Generic secrets are created and managed by the REST APIs in SAP AI Core and consumed securely in a workload.

-   For **non-sensitive** information:

    You can include non-sensitive parameters using configurations or labels.

    > ### Note:  
    > These parameters may be returned in clear text \(for example, in GET requests\).


