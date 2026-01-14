---
title: "Step 3. Specify Credentials and Protocol Type"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/netapp_add_creds.html"
last_updated: "4/17/2025"
product_version: "13.0.1.1071"
---

# Step 3. Specify Credentials and Protocol Type

In this article

At the Credentials step of the wizard, specify credentials for a user account with administrator privileges on the storage system, and select the communication protocol.

1. From the Credentials list, select credentials to connect to the storage system. If you have not set up credentials beforehand, click the Manage accounts link or click Add on the right of the Credentials field to add the credentials. For more information, see the [Credentials Manager](credentials_manager.md) section in the Veeam Backup & Replication User Guide.
2. From the Protocol list, select the type of protocol over which you want to communicate with the storage system: HTTP or HTTPs.

The default protocol is HTTPs. However, you can configure the storage system to communicate with Veeam Backup & Replication over the HTTP protocol if needed.

1. The default port for communication with the storage system is 443. If necessary, you can change the port number in storage system settings and specify the new port number in the Port field.

When you add a storage system, Veeam Backup & Replication saves to the configuration database a thumbprint of the TLS certificate installed on the NetApp management server. During every subsequent connection to the server, Veeam Backup & Replication uses the saved thumbprint to verify the server identity and avoid the man-in-the-middle attack.

If the certificate installed on the server is not trusted, Veeam Backup & Replication displays a warning.

* To view detailed information about the certificate, click View.
* If you trust the server, click Continue.
* If you do not trust the server, click Cancel.

Veeam Backup & Replication will display an error message, and you will not be able to connect to the server.

When you update a certificate on a server, this server becomes unavailable in the Veeam Backup & Replication console. To make the server available again, acknowledge the new certificate at the Credentials step of the edit storage system wizard.

![Step 3. Specify Credentials and Protocol Type](images/netapp_add_creds.webp)

Page updated 4/17/2025

Page content applies to build 13.0.1.1071
