---
title: "Rescanning Protected Computer"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_protected_computers_rescan.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---

# Rescanning Protected Computer


You can rescan protected computers added to the inventory. The rescan operation may be required, for example, if you want to refresh information about the protected computer in the Veeam Backup & Replication database. During the rescan operation, Veeam Backup & Replication communicates to Veeam Installer Service running on the protected computer, retrieves information about the computer and stores this information to the configuration database.

To rescan a protected computer:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical Infrastructure node and select the necessary protection group.
3. In the working area, select the computer and click Rescan on the ribbon or right-click the computer and select Rescan.

[![Rescan Protected Computer](images/mongo_protected_computer_rescan.webp)](images/mongo_protected_computer_rescan.webp "Rescan Protected Computer")


