<!-- loio30afaf560bce4b82933e789382c02860 -->

# Integrating SAP Business Data Cloud with SAP AI Core

Set up your embedded SAP Business Data Cloud Connect so that the SAP AI Core instance owned by your line of business can access data products directly.



## Context

Your line of business \(LoB\) application can use SAP AI Core to make tabular AI inference calls \(for example, using `SAP-RPT-1`\). These calls require context data such as few-shot examples or reference tables. The context data is to be provided from SAP Business Data Cloud products, which are already available to your LoB.

Your LoB application is already connected to SAP Business Data Cloud foundation services through SAP Business Data Cloud Connect, and consumes SAP BDC data products through this integration. Instead of having proxy context data at the time of the inference call, SAP AI Core can access the data products directly and therefore fetch its own context at inference time.

To allow access, you must adjust the setup of SAP Business Data Cloud Connect so that it can delegate access to the data products to the SAP AI Core instance in the LoB. Because SAP AI Core is a technical dependency of the LoB and not a standalone system, it remains invisible to the end customer at all times.



## Prerequisites

-   Your LoB already consumes data products via an embedded SAP Business Data Cloud Connect. It must consume the products from the HDLFS endpoint using its own mutual Transport Layer Security \(mTLS\) certificate or a delegate. For more information, see [BDC Connect Onboarding](https://pages.github.tools.sap/bigdataservices/Docs/services/partnerships/bdc-connect-onboarding/#embedded-bdc-connect).

    Specifically, you must have:

    -   Configured your embedded SAP Business Data Cloud Connect as an embedded tenant in the Unified Resource Manager \(URM\).
    -   Established a `BusinessIntegration` formation between the LoB and your embedded SAP Business Data Cloud Connect \(Formation 1: technical mTLS trust\).
    -   Registered the LoB as a subscriber to the Service Provider Integration Interface \(SPII\) subscriber for the app-to-app formation type.
    -   Joined an app-to-app formation with the producer of the SAP BDC foundation service data product \(Formation 2: data product consumption\).
    -   Implemented the three-wave SPII callback in the LoB application, consisting of Wave 0, Wave 1, and Wave 2.

-   The LoB has provisioned SAP AI Core as described under [Initial Setup](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/38c4599432d74c1d94e70f7c955a717d.html "Get started with SAP AI Core using the standard procedures for the SAP BTP, Cloud Foundry environment or Kyma environment.") :arrow_upper_right:.

    Specifically, you must have:

    -   Provisioned one instance of SAP AI Core for each LoB and region. That is, each LoB must operate its own, dedicated instance of SAP AI Core.
    -   Injected a **service key** for the service instance into the LoB application runtime.
    -   Established one SAP AI Core **resource group** for each LoB tenant or end customer. You establish the resource group when you onboard the tenant. The resource group is used to separate data.

-   Make sure that you've set the following headers:

    ****


    <table>
    <tr>
    <th valign="top">

    Header
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Authorization
    
    </td>
    <td valign="top">
    
    Bearer $TOKEN
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    AI-Resource-Group
    
    </td>
    <td valign="top">
    
    Resource group used in the activation steps
    
    </td>
    </tr>
    </table>
    

-   **[Grant SAP AI Core Access to Data Products](grant-sap-ai-core-access-to-data-products-8bd58cb.md "Adjust the integration process so that SAP AI Core can access data
    products through embedded SAP Business Data Cloud Connect using a delegation
    mechanism. This process involves extending SPII callback implementations and configuring data
    destinations, tabular artifacts, and scenario configurations across Wave 0 and Wave 2
    phases.")**  
Adjust the integration process so that SAP AI Core can access data products through embedded SAP Business Data Cloud Connect using a delegation mechanism. This process involves extending SPII callback implementations and configuring data destinations, tabular artifacts, and scenario configurations across Wave 0 and Wave 2 phases.

**Related Information**  


[Embedded BDC Connect](https://pages.github.tools.sap/bigdataservices/Docs/services/partnerships/bdc-connect-onboarding/#embedded-bdc-connect)

[Service Provider Integration Interface \(SPII\)](https://pages.github.tools.sap/atom-cfs/atom-docs/docs/product-concepts/customer-landscape/spii/)

[Tenant Mapping Contract](https://github.wdf.sap.corp/bigdataservices/bdc-partnerships/blob/main/docs/ucl/tenant-mapping-contract.md#embedded-bdc-connect-facilitating-data-product-consumption-by-intelligent-apps)

