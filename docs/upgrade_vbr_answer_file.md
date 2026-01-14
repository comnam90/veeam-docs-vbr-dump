---
title: "Upgrading Veeam Backup & Replication in Silent Mode"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/upgrade_vbr_answer_file.html"
last_updated: "6/25/2025"
product_version: "13.0.1.1071"
---

# Upgrading Veeam Backup & Replication in Silent Mode

In this article

You can upgrade Veeam Backup & Replication in the silent automated mode with a special XML answer file by using the command line interface. The answer file contains all the necessary upgrade settings in the proper order and their thorough description.

Before You Begin

Before starting the upgrade of Veeam Backup & Replication in the unattended mode with the answer file, consider the following:

* The user account that you use to run the silent installation must be in the local Administrators group on the machine where the silent installation will run. The silent installation cannot be run under the LocalSystem and NetworkService accounts.

* If the user account that you use to run the unattended upgrade is logged on the machine using the [network logon](https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/windows-logon-scenarios#BKMK_NetworkLogon) method, the unattended upgrade will fail. To avoid this, use an additional /SkipNetworkLogonErrors command line key. For example, it is required when the unattended upgrade is started within a remote PowerShell session.
* When configuring the answer file, remove or comment out unused [Optional] parameters. Otherwise, the upgrade session will fail.

Upgrading Veeam Backup & Replication

To upgrade Veeam Backup & Replication in the silent mode with the answer file, take the following steps:

1. Copy the VbrAnswerFile\_upgrade.xml file to your local drive.

You can find the template answer file on the Veeam Backup & Replication installation disk in the \Setup\Silent\AnswerFiles\VBR folder. This folder contains the following templates of answer files used for installing, uninstalling, and upgrading Veeam Backup & Replication:

* VbrAnswerFile\_install.xml — for installing Veeam Backup & Replication
* VbrAnswerFile\_uninstall.xml — for uninstalling Veeam Backup & Replication
* VbrAnswerFile\_upgrade.xml — for upgrading Veeam Backup & Replication

1. Configure upgrade parameters according to your needs. For details, see [Configuration Parameters](#ConfigurationParameters).

Check that the answer file has the correct bundle (Vbr) and mode (upgrade) specified in line 2:

|  |
| --- |
| <unattendedInstallationConfiguration bundle="Vbr" mode="upgrade" version="1.0"> |

1. After you make all the necessary changes in your answer file, start the upgrade by running the Veeam.Silent.Install.exe file located on the Veeam Backup & Replication installation disk in the \Setup\Silent folder. Use the following command line keys in your installation command:

|  |
| --- |
| D:\Setup\Silent\Veeam.Silent.Install.exe /AnswerFile E:\MyAnswerFileVBRUpgrade.xml /SkipNetworkLogonErrors |

where:

* /AnswerFile — required key for specifying the path to your custom answer file, for example: E:\MyAnswerFileVBRUpgrade.xml.
* /SkipNetworkLogonErrors — optional key that allows skipping additional pre-upgrade validations that do not work under the network logon, which will block the silent upgrade from running.
* /LogFolder — optional key for specifying the path where the setup should save log files if it is different from the default path. The default path is: C:\ProgramData\Veeam\Setup\Temp.

Configuration Parameters

The configuration file contains the following parameters:

| Parameter | Required? | Default | Description |
| --- | --- | --- | --- |
| ACCEPT\_EULA | Yes |  | Specify 1 to accept the Veeam license agreement. |
| ACCEPT\_LICENSING\_POLICY | Yes |  | Specify 1 to accept the Veeam licensing policy. |
| ACCEPT\_THIRDPARTY\_LICENSES | Yes |  | Specify 1 to accept the license agreement for 3rd party components that Veeam incorporates. |
| ACCEPT\_REQUIRED\_SOFTWARE | Yes |  | Specify 1 to accept all required software license agreements. |
| VBR\_LICENSE\_FILE | No |  | Specify the path to the license file on the machine where you want to install Veeam Backup & Replication. If you do not specify this parameter (or leave it empty value), Veeam Backup & Replication will be installed using the current license file. To install the Community Edition, set the parameter to 0. |
| VBR\_LICENSE\_AUTOUPDATE | No | 1 | Specify 1 to enable automatic license update and usage reporting. Specify 0 if you want to update the license manually. For Community Edition, NFR and Evaluation licenses, specify 1. For licenses without ID information, specify 0. |
| VBR\_SERVICE\_PASSWORD | No |  | Specify the password for the account under which the Veeam Backup Service will run. |
| VBR\_SQLSERVER\_PASSWORD | No |  | Specify the password to connect to the SQL Server in the SQL Server authentication mode. |
| VBR\_ENTRAID\_DATABASE\_INSTALL | No | 1 | Specify 1 to install a bundled PostgreSQL server for the Microsoft EntraID backup functionality. If set to 0, PostgreSQL database will not be installed for Microsoft EntraID backup. |
| VBR\_AUTO\_UPGRADE | No | 0 | Specify 1 to automatically upgrade existing components in the backup infrastructure. Specify 0 if you do not want Veeam Backup & Replication to upgrade the existing components automatically. |
| REBOOT\_IF\_REQUIRED | No | 0 | Specify 1 if you want to reboot the machine where you install Veeam Backup & Replication after the installation finishes. Specify 0 if you do not want to reboot the machine. |

Note that you must specify "1" in ACCEPT\_EULA, ACCEPT\_LICENSING\_POLICY, ACCEPT\_THIRDPARTY\_LICENSES and ACCEPT\_REQUIRED\_SOFTWARE parameters to proceed with the upgrade.

Upgrade Result Codes

The upgrade result is written into the upgrade log file located at your selected log folder. It may show one of the following result codes:

| Result Code | Result |
| --- | --- |
| 0 | success |
| 1603 | install failure |
| 3010 | reboot required |
| 3011 | logoff required |

Upgrade Error Codes

The upgrade error codes accompanied by their detailed description are displayed in the command line dialog. They can also be found in the UnattendedInstallationResult\_%DATE%\_%TIME%.xml file in the log folder (by default, C:\ProgramData\Veeam\Setup\Temp). You can use such an XML file for retrieving upgrade results from the scripts or utilities that are used to run the upgrade. The error message may show one of the following error codes:

| Error Code | Description |
| --- | --- |
| 0 | Installation has been completed successfully. |
| 1 | Product is already installed. |
| 2 | Uninstallation has been completed successfully. |
| 11 | Unable to start the setup program, because machine reboot is pending. |
| 12 | Reboot is required to finalize prerequisites installation. |
| 13 | Reboot is required to finalize the product installation. |
| 14 | Logoff is required to finalize the product installation. |
| 101 | Failed to start the installer. |
| 102 | Invalid answer file provided. |
| 103 | Invalid launch conditions. |
| 104 | Failed to initialize setup properties. |
| 105 | Failed to validate setup properties. |
| 106 | System configuration check detected some issues. |
| 107 | Failed to install prerequisites. |
| 108 | Failed to install a database server. |
| 109 | Failed to install the product. |
| 110 | Failed to update the product. |
| 111 | Failed to change a service status. |
| 112 | Failed to uninstall the product. |
| 113 | Unexpected error occurred. |

Page updated 6/25/2025

Page content applies to build 13.0.1.1071
