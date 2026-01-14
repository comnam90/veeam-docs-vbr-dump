---
title: "Windows Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pre_installed_agent_upgrade_windows.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Windows Computers

In this article

To update pre-installed Veeam Agent on a Microsoft Windows computer, perform the following operations:

1. Upload the Veeam Agent setup files on the computer you want to protect.
2. Uninstall obsolete version of the Veeam Installer Service. To do this, navigate to Control Panel > Programs > Programs and Features, find the Veeam Installer Service in the list of programs and uninstall it.

1. Install the prerequisite software located in the <path\_to\_setup\_files>/Windows/13.0.1.1009 folder.
2. Install the new version of Veeam Agent. Double-click the Veeam\_B&R\_Endpoint\_x64.msi file located in the <path\_to\_setup\_files>/Windows/13.0.1.1009/VAW folder.

1. If necessary, immediately synchronize Veeam Agent with Veeam Backup & Replication running the following command:

|  |
| --- |
| "C:\Program Files\Veeam\Endpoint Backup\Veeam.Agent.Configurator.exe" -syncnow |

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
