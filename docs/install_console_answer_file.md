---
title: "Installing Veeam Backup & Replication Console in Silent Mode"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/install_console_answer_file.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Installing Veeam Backup & Replication Console in Silent Mode

In this article

You can install the Veeam Backup & Replication console in the silent automated mode with a special XML answer file by using the command line interface. The answer file contains all the necessary installation settings in the proper order and their thorough description.

Before You Begin

Before starting the installation of the Veeam Backup & Replication console in the unattended mode with the answer file, consider the following:

* The user account that you use to run the silent installation must be in the local Administrators group on the machine where the silent installation will run. The silent installation cannot be run under the LocalSystem and NetworkService accounts.

* If the user account that you use to run the unattended installation is logged on the machine using the network logon method, the unattended installation will fail. To avoid this, use an additional /SkipNetworkLogonErrors command line key. For example, it is required when the unattended installation is started within a remote PowerShell session.
* When configuring the answer file, remove or comment out unused [Optional] parameters. Otherwise, the installation session will fail.

Installing Veeam Backup & Replication Console

To install the Veeam Backup & Replication console in the silent mode with the answer file, take the following steps:

1. Copy the VbrConsoleAnswerFile\_install.xml file to your local drive.

You can find the template answer file on the Veeam Backup & Replication installation disk in the \Setup\Silent\AnswerFiles\VBRConsole folder. This folder contains the following templates of answer files used for installing, uninstalling, and upgrading the Veeam Backup & Replication console:

* VbrConsoleAnswerFile\_install.xml — for installing the Veeam Backup & Replication console
* VbrConsoleAnswerFile\_uninstall.xml — for uninstalling the Veeam Backup & Replication console
* VbrConsoleAnswerFile\_upgrade.xml — for upgrading the Veeam Backup & Replication console

1. Configure installation parameters according to your needs. For details, see [Configuration Parameters](#ConfigurationParameters).

Check that the answer file has the correct bundle (VbrConsole) and mode (install) specified in line 2:

|  |
| --- |
| <unattendedInstallationConfiguration bundle="VbrConsole" mode="install" version="1.0"> |

1. After you make all the necessary changes in your answer file, start the installation by running the Veeam.Silent.Install.exe file located on the Veeam Backup & Replication installation disk in the \Setup\Silent folder. Use the following command line keys in your installation command:

|  |
| --- |
| D:\Setup\Silent\Veeam.Silent.Install.exe /AnswerFile E:\MyAnswerFileConsole.xml /SkipNetworkLogonErrors |

where:

* /AnswerFile — required key for specifying the path to your custom answer file, for example: E:\MyAnswerFileConsole.xml.
* /SkipNetworkLogonErrors — optional key that allows skipping additional pre-installation validations that do not work under the network logon, which will block the silent installation from running.
* /LogFolder — optional key for specifying the path where the setup should save log files if it is different from the default path. The default path is: C:\ProgramData\Veeam\Setup\Temp.

Configuration Parameters

The configuration file contains the following parameters:

| Parameter | Required? | Default | Description |
| --- | --- | --- | --- |
| ACCEPT\_EULA | Yes |  | Specify 1 to accept the Veeam license agreement. |
| ACCEPT\_LICENSING\_POLICY | Yes |  | Specify 1 to accept the Veeam licensing policy. |
| ACCEPT\_THIRDPARTY\_LICENSES | Yes |  | Specify 1 to accept the license agreement for 3rd party components that Veeam incorporates. |
| ACCEPT\_REQUIRED\_SOFTWARE | Yes |  | Specify 1 to accept all required software license agreements. |
| INSTALLDIR | No | %ProgramFiles%\Veeam\Backup and Replication | Specify the path to the directory where the Veeam Backup & Replication console will be installed. If you do not specify this parameter, the default %ProgramFiles%\Veeam\Backup and Replication installation path is used. |
| AHV\_INSTALL | No | 1 | Specify 1 if you want to install Veeam Plug-In for Nutanix AHV. Specify 0 if you do not want to install the plugin. |
| KVM\_INSTALL | No | 1 | Specify 1 if you want to install oVirt KVM Plug-In for Veeam Backup & Replication. Specify 0 if you do not want to install the plugin. |
| PVE\_INSTALL | No | 1 | Specify 1 if you want to install Veeam Plug-In for Proxmox VE. Specify 0 if you do not want to install the plugin. |
| SCP\_INSTALL | No | 1 | Specify 1 if you want to install Veeam Plug-In for Scale Computing HyperCore. Specify 0 if you do not want to install the plugin. |
| AWS\_INSTALL | No | 1 | Specify 1 if you want to install AWS Plug-In for Veeam Backup & Replication. Specify 0 if you do not want to install the plugin. |
| AZURE\_INSTALL | No | 1 | Specify 1 if you want to install Microsoft Azure Plug-In for Veeam Backup & Replication. Specify 0 if you do not want to install the plugin. |
| KASTEN\_INSTALL | No | 1 | Specify 1 if you want to install Veeam Kasten Plug-In for Veeam Backup & Replication. Specify 0 if you do not want to install the plugin. |
| REBOOT\_IF\_REQUIRED | No | 0 | Specify 1 if you want to reboot the machine where you install Veeam Backup & Replication after the installation finishes. Specify 0 if you do not want to reboot the machine. |

Note that you must specify "1" in ACCEPT\_EULA, ACCEPT\_LICENSING\_POLICY, ACCEPT\_THIRDPARTY\_LICENSES and ACCEPT\_REQUIRED\_SOFTWARE parameters to proceed with the installation.

Installation Result Codes

The installation result is written into the installation log file located at your selected log folder. It may show one of the following result codes:

| Result Code | Result |
| --- | --- |
| 0 | success |
| 1603 | install failure |
| 3010 | reboot required |
| 3011 | logoff required |

Installation Error Codes

The installation error codes accompanied by their detailed description are displayed in the command line dialog. They can also be found in the UnattendedInstallationResult\_%DATE%\_%TIME%.xml file in the log folder (by default, C:\ProgramData\Veeam\Setup\Temp). You can use such an XML file for retrieving installation results from the scripts or utilities that are used to run the installation. The error message may show one of the following error codes:

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

Page updated 11/10/2025

Page content applies to build 13.0.1.1071
