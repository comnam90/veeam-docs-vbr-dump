---
title: "Step 1. Launch Instant Recovery Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_ir_multiple_latest_wizard.html"
last_updated: "8/19/2025"
product_version: "13.0.1.1071"
---

# Step 1. Launch Instant Recovery Wizard


To perform instant recovery of multiple databases to the latest state, do the following:

1. In the navigation pane, select the Oracle server or an Oracle home.
2. On the Server or Oracle Home tab, select Instant Recovery > Instant Recovery of the latest state to <original\_location>.

Alternatively, you can right-click the Oracle server or an Oracle home and select Instant Recovery > Instant recovery of the latest state to <original\_location>.

|  |
| --- |
| Note |
| The name of the instant recovery option depends on the restore point you select during the [application item restore](restore_veeam_explorers.md) process in the Veeam Backup & Replication console.   * If you select the most recent available restore point, the option name is displayed as Instant recovery of the latest state to <original\_location>. * If you select any other restore point, the option name is displayed as Instant recovery of the state of <point\_in\_time> to <original\_location>. |

[For Windows-based Oracle servers] If the user specified in the job is not the Oracle home user, you must provide a password to access the target Oracle home. Applicable to Oracle 12c and later versions.

[![Performing Instant Recovery of Latest State](images/veor_ir_multiple_latest.webp)](images/veor_ir_multiple_latest.webp "Performing Instant Recovery of Latest State")


