---
title: "Deployment Procedure for Windows Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/appendix_a_centralized_hotfix_deployment_windows.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Deployment Procedure for Windows Computers

In this article

To deploy a hotfix on Microsoft Windows computers included in the protection group, perform the following steps:

1. Obtain a hotfix from Veeam Customer Support.
2. Save the Veeam Agent for Microsoft Windows setup archive to the following folder on the server where Veeam Backup & Replication console is installed:

|  |
| --- |
| C:\ProgramData\Veeam\Agents\fixes\vaw\kb.<number> |

where <number> is a number of the hotfix provided by Veeam Customer Support.

1. Rescan the protection group:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical and Cloud Infrastructure node.
3. In the inventory pane, select the necessary protection group and click Rescan on the ribbon or right-click the protection group and select Rescan.

[![Deploy Hotfix on Microsoft Windows Computers](images/protection_group_rescan.webp)](images/protection_group_rescan.webp "Deploy Hotfix on Microsoft Windows Computers")

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
