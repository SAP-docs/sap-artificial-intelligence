<!-- copy76b3685920164bbeaa17556e128b93af -->

# Generic Secrets for Grounding

The grounding module in SAP AI Core connects to external document repositories through generic secrets. These secrets store the credentials and connection details required to access repository content used in retrieval and grounding pipelines.

The grounding module in SAP AI Core supports the following data repositories:

-   Microsoft SharePoint

-   AWS S3

-   SFTP

-   SAP Build Work Zone

-   SAP Document Management service


Each repository type supports specific authentication methods. For Microsoft SharePoint, both `OAuth2Password` and `OAuth2ClientCredentials` authentication are supported. AWS S3 and SFTP use `NoAuthentication`. Although this authentication type is listed as `NoAuthentication`, the implementation still performs a basic authentication check for security purposes.

You must onboard at least one repository to enable grounding. For detailed onboarding instructions, see:

-   [Grounding Generic Secrets for Microsoft SharePoint](grounding-generic-secrets-for-microsoft-sharepoint-0cd2b30.md).
-   [Grounding Generic Secrets for AWS S3](grounding-generic-secrets-for-aws-s3-15eb50b.md).
-   [Grounding Generic Secrets for SFTP](grounding-generic-secrets-for-sftp-4085952.md).
-   [Grounding Generic Secrets for SAP Build Work Zone](grounding-generic-secrets-for-sap-build-work-zone-8737ceb.md).

The grounding module also supports metadata, which provides additional information about repositories for document indexing and contextualization. Metadata onboarding uses the `OAuth2ClientCredentials` authentication type and can be configured alongside any repository. For more information, see [Generic Secrets for Contextualization with Metadata](generic-secrets-for-contextualization-with-metadata-dade07e.md).

-   **[Grounding Generic Secrets for Microsoft SharePoint](grounding-generic-secrets-for-microsoft-sharepoint-56d80e4.md "Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories
    and tools, without compromising your credentials.")**  
Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.
-   **[Grounding Generic Secrets for AWS S3](grounding-generic-secrets-for-aws-s3-6ae421f.md "Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories
    and tools, without compromising your credentials.")**  
Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.
-   **[Grounding Generic Secrets for SFTP](grounding-generic-secrets-for-sftp-47ec325.md "Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories
    and tools, without compromising your credentials.")**  
Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.
-   **[Grounding Generic Secrets for SAP Build Work Zone](grounding-generic-secrets-for-sap-build-work-zone-2a9a95a.md "Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories
    and tools, without compromising your credentials.")**  
Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.
-   **[Grounding Generic Secrets for SAP Document Management Service](grounding-generic-secrets-for-sap-document-management-service-9bc02ba.md "")**  


