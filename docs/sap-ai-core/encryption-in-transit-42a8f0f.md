<!-- loio42a8f0fd505d4fdca3ed1dc1de14ca07 -->

# Encryption in Transit

Communication with the service, including data upload and download, is encrypted using the transport layer security \(TLS\) protocol. SAP services support only the latest protocol versions \(that is, TLS v1.2 and later\) and strong cipher suites. Your systems must use the supported protocol versions and cipher suites to set up secure communication with the services. They must also validate the certificates against the services’ domain names to avoid man-in-the-middle attacks.

