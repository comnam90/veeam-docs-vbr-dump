---
title: "Deployment Procedure for Unix Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/appendix_a_centralized_hotfix_deployment_unux.html"
last_updated: "11/5/2025"
product_version: "13.0.1.1071"
---

# Deployment Procedure for Unix Computers

In this article

You can add Unix-based servers with Veeam Agent for IBM AIX or Veeam Agent for Oracle Solaris installed to protection groups for individual computers.

To deploy a hotfix on Unix machines included in the protection group, perform the following steps:

1. Obtain a hotfix from Veeam Customer Support.
2. In the C:\ProgramData\Veeam\Agents\vau folder on the Veeam backup server, replace the original Veeam Agent for Unix package with the hotfix package.

1. Rescan the protection group:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical and Cloud Infrastructure node.
3. In the inventory pane, select the necessary protection group and click Rescan on the ribbon or right-click the protection group and select Rescan.

During rescan, Veeam Backup & Replication will update Veeam Agents on the protected machines.

Page updated 11/5/2025

Page content applies to build 13.0.1.1071
