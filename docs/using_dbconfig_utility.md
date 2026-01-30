---
title: "Using Veeam Configuration Database Connection Utility in Veeam Backup & Replication for Windows"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/using_dbconfig_utility.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Using Veeam Configuration Database Connection Utility in Veeam Backup & Replication for Windows


You can launch the configuration database connection utility the following ways:

* From the Start menu by clicking Configuration Database Connection Settings.
* By using the Veeam.Backup.DBConfig.exe file located in the installation folder. The default path to the folder is the following: %PROGRAMFILES%\Common Files\Veeam\Backup and Replication\DBConfig.
* By using the Veeam.Backup.DBConfig.exe file located in the ISO file. The path to the file is the following: %ISO%:\Tools\DBConfig.

To run the utility, you must have administrative rights on the local machine, as long as the utility makes changes to the registry. If prompted at the launch, choose Run as administrator.

To manage connection settings for Veeam Backup & Replication, check [prerequisites](dbconfig_before_you_begin.md) and use the launched Veeam Backup & Replication Configuration Database Connection Settings wizard.

1. [Select the product](dbconfig_product.md).
2. [Specify database connection settings](dbconfig_connection_settings.md).
3. [Apply connection settings](dbconfig_apply.md).
4. [Finish working with the wizard](dbconfig_summary.md).


