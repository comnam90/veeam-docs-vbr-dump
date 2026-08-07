---
title: "Step 3. Enter Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_server_add_credentials.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Enter Credentials


At the Credentials step of the wizard, specify credentials of an account that will be used to access the Sangfor Cloud Platform.

For credentials to be displayed in the Credentials list, they must be added to the Credentials Manager as described in section [Credentials Manager](credentials_manager_linux.md). If you have not added the necessary credentials to the Credentials Manager beforehand, you can do this without closing the New Sangfor aSV Server wizard. To do that, click either the Manage accounts link or the Add button, and specify the user name, password and description in the Credentials window.

After you click Apply, the backup server will connect to the Sangfor Cloud Platform and check its TLS certificate. If the certificate is not installed on the backup server, the Certificate Security Alert Window will display a warning notifying that secure communication cannot be guaranteed. To allow the backup server to connect to the Sangfor Cloud Platform using the certificate, click Continue.

![Step 3. Enter Credentials](images/sangfor_server_add_credentials.webp)

Page updated 2026-07-14

