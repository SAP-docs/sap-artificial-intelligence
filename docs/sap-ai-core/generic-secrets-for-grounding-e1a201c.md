<!-- loioe1a201c1fc2e4eb3a570efd81a3b3616 -->

# Generic Secrets for Grounding



The following data repositories are supported in the grounding module:

-   Microsoft SharePoint

-   AWS S3

-   SFTP

-   SAP Build Work Zone

-   SAP Document Management service


The following authentication types for each document repository type:

-   Microsoft SharePoint
    -   OAuth2Password

    -   OAuth2ClientCredentials


-   AWS S3
    -   NoAuthentication

        > ### Note:  
        > Although the authentication type is `NoAuthentication`, the implementation includes a basic authentication check.


-   SFTP
    -   NoAuthentication

        > ### Note:  
        > Although the authentication type is `NoAuthentication`, the implementation includes a basic authentication check.



Metadata is also supported. Metadata stores additional details about the repository that can be used during document indexing. The following authentication types are available for metadata:

-   OAuth2ClientCredentials


You need to onboard a minimum one repository for grounding.

To onboard a Microsoft SharePoint repository, see [Grounding Generic Secrets for Microsoft SharePoint](grounding-generic-secrets-for-microsoft-sharepoint-0cd2b30.md)

To onboard a AWS S3 repository, see [Grounding Generic Secrets for AWS S3](grounding-generic-secrets-for-aws-s3-15eb50b.md)

To onboard a SFTP repository, see [Grounding Generic Secrets for SFTP](grounding-generic-secrets-for-sftp-4085952.md)

To onboard a WorkZone repository, see [Grounding Generic Secrets for WorkZone](grounding-generic-secrets-for-workzone-8737ceb.md)

Metadata is an optional extra, that can be used alongside the repository of your choice.

To onboard metadata, see [Generic Secrets for Contextualization with Metadata](generic-secrets-for-contextualization-with-metadata-dade07e.md)

-   **[Grounding Generic Secrets for Microsoft SharePoint](grounding-generic-secrets-for-microsoft-sharepoint-0cd2b30.md "Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories
    and tools, without compromising your credentials.")**  
Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.
-   **[Grounding Generic Secrets for AWS S3](grounding-generic-secrets-for-aws-s3-15eb50b.md "Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories
    and tools, without compromising your credentials.")**  
Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.
-   **[Grounding Generic Secrets for SFTP](grounding-generic-secrets-for-sftp-4085952.md "Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories
    and tools, without compromising your credentials.")**  
Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.
-   **[Grounding Generic Secrets for WorkZone](grounding-generic-secrets-for-workzone-8737ceb.md "Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories
    and tools, without compromising your credentials.")**  
Your cloud storage credentials are managed using secrets. Secrets are a means of allowing and controlling connections across directories and tools, without compromising your credentials.
-   **[Grounding Generic Secrets for SAP Document Management Service](grounding-generic-secrets-for-sap-document-management-service-f8919a4.md "")**  


