---
title: "Step 1. Launch Restore Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_restore_single_pit_wizard.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Step 1. Launch Restore Wizard


To launch the Restore wizard, do the following:

1. In the navigation pane, select a database.
2. On the Database tab, select Restore Database > Restore point-in-time state.

Alternatively, you can right-click a database and select Restore database > Restore point-in-time state.

|  |
| --- |
| Important |
| The point-in-time restore option is only available if the ARCHIVELOG mode is enabled. |

[For Data Guard restore] Veeam Explorer for Oracle restores the primary node first and then uses it to restore the remaining nodes and the Data Guard infrastructure. This sequence is the same even if you launch restore from a standby node.

[![Launching Restore Wizard](images/point_in_time.webp)](images/point_in_time.webp "Launching Restore Wizard")


