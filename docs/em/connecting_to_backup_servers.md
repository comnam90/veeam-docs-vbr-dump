---
title: "connecting_to_backup_servers"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/connecting_to_backup_servers.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---


In this article

When communicating with backup servers, Veeam Backup Enterprise Manager uses a TLS certificate for authentication so that Veeam Backup Enterprise Manager does not store backup server account credentials. For connections with backup servers with earlier versions of Veeam Backup & Replication, Veeam Backup Enterprise Manager uses backup server account credentials for authentication.

Certificate-based connection works in the following way:

1. When adding a backup server, you specify connection settings including an account with Veeam Backup Administrator role assigned on the backup server.

For more information, see [Adding Backup Servers](adding_backup_server.md).

1. Veeam Backup Enterprise Manager sends the credentials as well as the certificate thumbprint that will be used by Veeam Backup Enterprise Manager Service and Veeam Guest Catalog Service for authentication.
2. Veeam Backup & Replication validates the credentials and saves Enterprise Manager data including the certificate thumbprint.
3. Veeam Backup & Replication sends its certificate thumbprint to Enterprise Manager.

For more information on managing backup server certificates, see the [Backup Server Certificate](https://helpcenter.veeam.com/docs/vbr/userguide/backup_server_certificate.html?ver=13) section of the Veeam Backup & Replication User Guide.

1. You validate the certificate. If you trust the certificate, Enterprise Manager adds the backup server to the infrastructure and saves the thumbprint to the database.

If a backup server is not available at the moment, Enterprise Manager stores the backup server account credentials until the connection is established. Then the credentials are deleted from the Enterprise Manager database.

1. The next time Enterprise Manager connects to Veeam Backup & Replication, the Enterprise Manager certificate is used for authentication.
2. If a backup server certificate is updated, you will have to validate it from Enterprise Manager. Until you validate the certificate, Enterprise Manager cannot collect data from the backup server.
3. Thirty days before the Enterprise Manager certificate is expired, you are prompted to update it.

For more information, see [Installing Certificates](updating_security_certificate.md).

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
