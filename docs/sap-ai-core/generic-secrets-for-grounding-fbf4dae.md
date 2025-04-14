<!-- loiofbf4daea78e9409eb13c4b413345a2c9 -->

# Generic Secrets for Grounding



The following data repositories are supported in the grounding module:

-   Microsoft SharePoint
-   AWS S3
-   SFTP

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

To onboard a Microsoft SharePoint repository, see [Grounding Generic Secrets for Microsoft SharePoint](grounding-generic-secrets-for-microsoft-sharepoint-bdea357.md)

To onboard a AWS S3 repository, see [Grounding Generic Secrets for AWS S3](grounding-generic-secrets-for-aws-s3-526b0ba.md)

To onboard a SFTP repository, see [Grounding Generic Secrets for SFTP](grounding-generic-secrets-for-sftp-45a4f39.md)

Metadata is an optional extra, that can be used alongside the repository of your choice.

To onboard metadata, see [Generic Secrets for Contextualization](generic-secrets-for-contextualization-97779db.md)

-   **[Grounding Generic Secrets for Microsoft SharePoint](grounding-generic-secrets-for-microsoft-sharepoint-bdea357.md "")**  

-   **[Grounding Generic Secrets for AWS S3](grounding-generic-secrets-for-aws-s3-526b0ba.md "")**  

-   **[Grounding Generic Secrets for SFTP](grounding-generic-secrets-for-sftp-45a4f39.md "")**  


