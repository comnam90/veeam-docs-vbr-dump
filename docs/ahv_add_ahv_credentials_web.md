---
title: "Step 3. Specify Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_add_ahv_credentials_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Credentials


At the Credentials step of the wizard, specify credentials for an administrator account with the Prism Admin role that is used to access the cluster or Prism Central. For more information on Nutanix AHV system administrator roles, see [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Nutanix-Security-Guide-v7_3:ssp-ssp-role-based-access-control-pc-c.html).

For credentials to be displayed in the Credentials list, they must be added to the Credentials Manager as described in section [Standard Accounts](credentials_manager_windows.md). If you have not added the necessary credentials to the Credentials Manager beforehand, you can do this without closing the New Nutanix AHV Sever wizard. To do that, click either the Manage accounts link or the Add button, and specify the user name, password and description in the Credentials window.

The backup server will connect to the cluster or Prism Central and check its TLS certificate. If the certificate is not trusted, the Untrusted Certificate window will display a warning notifying that secure communication cannot be guaranteed. To allow the backup server to connect to the cluster or Prism Central using the certificate, click Trust and Continue.

[![Rescanning Nutanix AHV Cluster](images/ahv_add_ahv_cluster_credentials_web.webp)](images/ahv_add_ahv_cluster_credentials_web.webp "Rescanning Nutanix AHV Cluster")

Page updated 2026-07-07

