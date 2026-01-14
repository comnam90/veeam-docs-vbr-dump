---
title: "Uninstalling Veeam Backup & Replication Console in Silent Mode"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uninstall_console_answer_file.html"
last_updated: "7/21/2025"
product_version: "13.0.1.1071"
---

# Uninstalling Veeam Backup & Replication Console in Silent Mode

In this article

You can uninstall the Veeam Backup & Replication console in the silent automated mode with a special XML answer file by using the command line interface. The answer file contains all the necessary uninstallation settings in the proper order and their thorough description.

Before You Begin

Before starting the uninstallation of the Veeam Backup & Replication console in the unattended mode with the answer file, consider the following:

* The user account that you use to run the silent installation must be in the local Administrators group on the machine where the silent installation will run. The silent installation cannot be run under the LocalSystem and NetworkService accounts.

* If the user account that you use to run the unattended uninstallation is logged on the machine using the [network logon](https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/windows-logon-scenarios#BKMK_NetworkLogon) method, the unattended uninstallation will fail. To avoid this, use an additional /SkipNetworkLogonErrors command line key. For example, it is required when the unattended uninstallation is started within a remote PowerShell session.
* When configuring the answer file, remove or comment out the unused [Optional] parameter. Otherwise, the uninstallation session will fail.

Uninstalling Veeam Backup & Replication Console

To uninstall the Veeam Backup & Replication console in the silent mode with the answer file, take the following steps:

1. Copy the VbrAnswerFile\_uninstall.xml file to your local drive.

You can find the template answer file on the Veeam Backup & Replication installation disk in the \Setup\Silent\AnswerFiles\VBRConsole folder. This folder contains the following templates of answer files used for installing, uninstalling, and upgrading Veeam Backup & Replication:

* VbrConsoleAnswerFile\_install.xml — for installing the Veeam Backup & Replication console
* VbrConsoleAnswerFile\_uninstall.xml — for uninstalling the Veeam Backup & Replication console
* VbrConsoleAnswerFile\_upgrade.xml — for upgrading the Veeam Backup & Replication console

1. Configure uninstallation parameters according to your needs. For details, see [Configuration Parameters](#ConfigurationParameters).

Check that the answer file has the correct bundle (VbrConsole) and mode (uninstall) specified in line 2:

|  |
| --- |
| <unattendedInstallationConfiguration bundle="VbrConsole" mode="uninstall" version="1.0"> |

1. After you make all the necessary changes in your answer file, start the uninstallation by running the Veeam.Silent.Install.exe file located on the Veeam Backup & Replication installation disk in the \Setup\Silent folder. Use the following command line keys in your uninstallation command:

|  |
| --- |
| D:\Setup\Silent\Veeam.Silent.Install.exe /AnswerFile E:\MyAnswerFileConsoleUninstall.xml /SkipNetworkLogonErrors |

where:

* /AnswerFile — required key for specifying the path to your custom answer file, for example: E:\MyAnswerFileConsoleUninstall.xml.
* /SkipNetworkLogonErrors — optional key that allows skipping additional pre-uninstallation validations that do not work under the network logon, which will block the silent uninstallation from running.
* /LogFolder — optional key for specifying the path where the setup should save log files if it is different from the default path. The default path is: C:\ProgramData\Veeam\Setup\Temp.

Configuration Parameters

The configuration file contains only the following parameter:

| Parameter | Required? | Default | Description |
| --- | --- | --- | --- |
| REBOOT\_IF\_REQUIRED | No | 0 | Specify 1 if you want to reboot the machine where you uninstall the Veeam Backup & Replication console after the uninstallation finishes. Specify 0 if you do not want to reboot the machine. |

Uninstallation Result Codes

The uninstallation result is written into the uninstallation log file located at your selected log folder. It may show one of the following result codes:

| Result Code | Result |
| --- | --- |
| 0 | success |
| 1603 | install failure |
| 3010 | reboot required |
| 3011 | logoff required |

Uninstallation Error Codes

The uninstallation error codes accompanied by their detailed description are displayed in the command line dialog. They can also be found in the UnattendedInstallationResult\_%DATE%\_%TIME%.xml file in the log folder (by default, C:\ProgramData\Veeam\Setup\Temp). You can use such an XML file for retrieving uninstallation results from the scripts or utilities that are used to run the uninstallation. The error message may show one of the following error codes:

| Error Code | Description |
| --- | --- |
| 2 | Uninstallation has been completed successfully. |
| 11 | Unable to start the setup program, because machine reboot is pending. |
| 101 | Failed to start the installer. |
| 102 | Invalid answer file provided. |
| 103 | Invalid launch conditions. |
| 112 | Failed to uninstall the product. |
| 113 | Unexpected error occurred. |

Page updated 7/21/2025

Page content applies to build 13.0.1.1071
