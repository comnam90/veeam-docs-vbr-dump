---
title: "Manual Recovery Verification"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_manual.html"
last_updated: "4/29/2025"
product_version: "13.0.1.1071"
---

# Manual Recovery Verification

In this article

Beside automatic recovery verification, you can perform manual verification of machine backups. Manual verification can be performed with all editions of Veeam Backup & Replication.

Boot Test

To perform a machine boot test, perform Instant Recovery for the verified machine. Power on the machine but do not connect the machine to the production network to avoid conflicts with the original machine.

Application Test

To perform an application test:

1. Create an isolated network.
2. Use the Instant Recovery wizard to restore the verified machine. At the Ready to Apply step of the wizard, clear the Connect VM to network check box.
3. When the machine is started, connect it to the isolated network.

The same procedure must be performed for all machines that run applications on which the verified machine is dependent such as domain controller and DNS. All machines must be connected to the same isolated network and started in the correct order: for example, DNS > domain controller > verified machine.

Page updated 4/29/2025

Page content applies to build 13.0.1.1071
