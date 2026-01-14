---
title: "Step 3. Specify Server Credentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_restore_multiple_tas_specify_server_credentials.html"
last_updated: "8/22/2023"
product_version: "13.0.1.1071"
---

# Step 3. Specify Server Credentials

In this article

At this step of the wizard, specify the connection parameters for the target SAP HANA server.

1. In the Server field, specify the DNS name or IP address of the target SAP HANA server.
2. In the SAP System field, specify the name (SID) of the target SAP HANA system.
3. In the OS User field, specify the operating system user (<sid>adm).
4. In the Password field, specify the password for the operating system user.
5. In the Protocol drop-down list, select the protocol that Veeam Explorer for SAP HANA will use to connect to SAP Web Services, which are then used to control the target SAP HANA system.

* Select HTTPS to establish a secure connection to the target server. Selecting this option will import 2 certificates issued by the target server to the backup server (2 certificates per host in multiple-host systems). The first certificate is used to securely connect to the SAP Control web service and the second to the SAP Start web service. Before proceeding with the Restore wizard, Veeam Explorer for SAP HANA will prompt you to review each certificate in a separate Certificate Security Alert dialog box.

* Select the Do not prompt for connections to <host\_name:port> check box if you want to use the certificate in future restore operations to the specified server. The certificate thumbprint will be saved to a Config.xml file, located in the UserProfile%\AppData\Local\Veeam\Backup\SapHanaExplorer directory on the machine where Veeam Explorer for SAP HANA is running.
* Click View Certificate... to see more details about the imported certificate.

[![Reviewing Certificate](images/vehana_license_review.webp)](images/vehana_license_review.webp "Reviewing Certificate")

* Select HTTP only if you want to quickly restore SAP HANA data and your backup infrastructure requires minimal security precautions. Selecting this option will not import any certificates from the target server to the backup server or give any prompts.

For more information about the ports used to connect to SAP Web Services, see [Ports](vehana_used_ports.md).

[![Specifying Target Server Credentials](images/vehana_specify_server_credentials_tas.webp)](images/vehana_specify_server_credentials_tas.webp "Specifying Target Server Credentials")

Page updated 8/22/2023

Page content applies to build 13.0.1.1071
