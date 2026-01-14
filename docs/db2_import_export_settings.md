---
title: "Exporting and Importing Plug-In Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_import_export_settings.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Exporting and Importing Plug-In Settings

In this article

You can export a Veeam Plug-In configuration file and apply the plug-in settings to other servers.

|  |
| --- |
| Important |
| The password included in the configuration file is encrypted. Thus, after you import the configuration file, you must set the credentials manually in the Veeam Plug-In configuration wizard or using DB2ConfigTool. |

To export the configuration file to another server, do the following:

1. On the server where Veeam Plug-In is installed, navigate to the /opt/veeam/VeeamPluginforDB2 directory.
2. Copy the veeam\_config.xml file to the server where you want to configure the plug-in.
3. Install Veeam Plug-In on the new server and place the copied XML file in the /opt/veeam/VeeamPluginforDB2 directory.
4. Set new credentials to connect to the Veeam Backup & Replication server using the following command:

|  |
| --- |
| DB2ConfigTool --set-credentials "serv02\Administrator" password |

Page updated 3/27/2025

Page content applies to build 13.0.1.1071
