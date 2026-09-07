<!-- loio9572098efa5d4c7ebf827684c423265a -->

# Encryption of Data

SAP AI Core encrypts customer data using tenant-specific encryption keys and integrates with SAP Data Custodian Key Management Service \(KMS\) to support customer-managed root encryption keys.

SAP AI Core integrates with SAP Data Custodian Key Management Service \(KMS\). You can use KMS to supply your own root encryption keys and manage customer-managed key \(CMK\) keychains.

For more information, see [SAP Data Custodian Key Management Service](https://help.sap.com/docs/sap-data-custodian/key-management-service/what-is-key-management-service-page).

Data created in SAP AI Core is automatically encrypted using tenant-specific data encryption keys \(L4\). The L4 keys are encrypted by key encryption keys \(L2 and L3\), which are protected by the customer-supplied root keys \(L1\).

> ### Note:  
> Disabling a root key can affect SAP AI Core operations:
> 
> -   Data encrypted with the key becomes inaccessible.
> -   Data currently being processed cannot be persisted.
> -   Connected systems may experience service disruptions.

> ### Note:  
> If no root key is provided through Key Management Service, SAP AI Core continues to encrypt data using tenant-specific data encryption keys.



## Encrypted Data in SAP AI Core

The following data is encrypted using tenant-specific client-side \(L4\) encryption keys:

-   Data Destination: configuration

-   Tabular Artifact: path, CSN document, CSN document reference path

-   Workflow templates
-   Serving templates

