---
title: "Automating Configuration of Plug-In for SAP HANA"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/saphana_config_automation.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Automating Configuration of Plug-In for SAP HANA

In this article

To automate the configuration of Veeam Plug-In for SAP HANA, do the following:

1. From the /opt/veeam/VeeamPluginforSAPHANA directory on the machine where Veeam Plug-In is installed, copy the Veeam Plug-In configuration file (veeam\_config.xml) to other servers where you want to configure the plug-in.
2. The password stored in the configuration file is encrypted with a machine key. Thus, on each machine, after the veeam\_config.xml file was copied, you must reset the password of the account used to log in to the Veeam Backup & Replication server. To reset the password, use the following command. Note that the operation requires root privileges.

|  |
| --- |
| SapBackintConfigTool --set-credentials <"serv\username"> <password> |

Page updated 3/27/2025

Page content applies to build 13.0.1.1071
