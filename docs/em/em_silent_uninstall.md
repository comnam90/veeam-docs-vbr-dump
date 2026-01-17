---
title: "Uninstalling Enterprise Manager in Silent Mode"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_silent_uninstall.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Uninstalling Enterprise Manager in Silent Mode


You can uninstall Veeam Backup Enterprise Manager in the silent mode with a special XML answer file by using the command line interface. The answer file contains all the necessary uninstallation settings in the proper order and their thorough description.

Before You Begin

Before starting the uninstallation of Veeam Backup Enterprise Manager in the silent mode, consider the following:

* The user account that you use to run the silent uninstallation must be in the local Administrators group on the machine where the silent uninstallation will run. The silent uninstallation cannot be run under the LocalSystem and NetworkService accounts.

* If the user account that you use to run the silent uninstallation is logged on the machine using the [network logon](https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/windows-logon-scenarios#BKMK_NetworkLogon) method, the silent uninstallation will fail. To avoid this, use an additional /SkipNetworkLogonErrors command line key. For example, it is required when the silent uninstallation is started using a remote PowerShell session.
* When configuring the answer file, remove or comment out unused [Optional] parameters. Otherwise, the uninstallation session will fail.

Uninstalling Veeam Backup Enterprise Manager

To uninstall Veeam Backup Enterprise Manager in the silent mode with the answer file, take the following steps:

1. Copy the EmAnswerFile\_uninstall.xml file to your local drive.

You can find the template answer file on the Veeam Backup & Replication installation disk in the \Setup\Silent\AnswerFiles\EM folder.

1. Configure uninstallation parameters according to your needs. For details, see [Configuration Parameters](#ConfigurationParameters).

Check that the answer file has the correct bundle (Em) and mode (uninstall) specified in line 2:

|  |
| --- |
| <unattendedInstallationConfiguration bundle="Em" mode="uninstall" version="1.0"> |

1. After you make all the necessary changes in your answer file, start the uninstallation by running the Veeam.Silent.Install.exe file located on the Veeam Backup Enterprise Manager installation disk in the \Setup\Silent folder. Use the following command line keys in your command:

|  |
| --- |
| D:\Setup\Silent\Veeam.Silent.Install.exe /AnswerFile E:\MyAnswerFileEMIninstall.xml /SkipNetworkLogonErrors |

where:

* /AnswerFile — required key for specifying the path to your custom answer file, for example: E:\MyAnswerFileEMUninstall.xml.
* /SkipNetworkLogonErrors — optional key that allows skipping additional pre-installation validations that do not work under the network logon, which will block the silent installation from running.
* /LogFolder — optional key for specifying the path where the setup should save log files if it is different from the default path. The default path is: C:\ProgramData\Veeam\Setup\Temp.

Configuration Parameters

The configuration file contains the following parameters:

| Parameter | Required? | Default | Description |
| --- | --- | --- | --- |
| REBOOT\_IF\_REQUIRED | No | 0 | Specify 1 if you want to reboot the machine where you uninstall Veeam Backup & Replication after the uninstallation finishes. Specify 0 if you do not want to reboot the machine. |

Uninstallation Result Codes

The installation result is written into the installation log file located at your selected log folder. It may show one of the following result codes:

| Result Code | Result |
| --- | --- |
| 0 | success |
| 1603 | install failure |
| 3010 | reboot required |
| 3011 | logoff required |

Uninstallation Error Codes

The installation error codes accompanied by their detailed description are displayed in the command line dialog. They can also be found in the UnattendedInstallationResult\_%DATE%\_%TIME%.xml file in the log folder (by default, C:\ProgramData\Veeam\Setup\Temp). The error message may show one of the following error codes:

| Error Code | Description |
| --- | --- |
| 1 | Product is already installed. |
| 2 | Uninstallation has been completed successfully. |
| 11 | Unable to start the setup program, because machine's reboot is pending. |
| 101 | Failed to start the installer. |
| 102 | Invalid answer file provided. |
| 103 | Invalid launch conditions. |
| 112 | Failed to uninstall the product. |
| 113 | Unexpected error occurred. |


