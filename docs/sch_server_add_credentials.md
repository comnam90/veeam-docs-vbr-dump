---
title: "Step 3. Enter Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_server_add_credentials.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Step 3. Enter Credentials


At the Credentials step of the wizard, specify credentials of an account that will be used to access the Scale Computing HyperCore cluster.

For credentials to be displayed in the Credentials list, they must be added to the Credentials Manager as described in section [Standard Accounts](https://helpcenter.veeam.com/docs/backup/vsphere/credentials_manager_windows.html?ver=120). If you have not added the necessary credentials to the Credentials Manager beforehand, you can do this without closing the New Scale Computing HyperCore Cluster wizard. To do that, click either the Manage accounts link or the Add button, and specify the user name, password and description in the Credentials window.

After you click Apply, the backup server will connect to the Scale Computing HyperCore cluster and check its TLS certificate. If the certificate is not installed on the backup server, the Certificate Security Alert Window will display a warning notifying that secure communication cannot be guaranteed. To allow the backup server to connect to the Scale Computing HyperCore cluster using the certificate, click Continue.

[![Providing Credentials to Access Scale Computing HyperCore Cluster](images/sch_server_add_credentials.webp)](images/sch_server_add_credentials.webp "Providing Credentials to Access Scale Computing HyperCore Cluster")


