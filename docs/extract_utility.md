---
title: "Extract Utility"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/extract_utility.html"
last_updated: "2/20/2025"
product_version: "13.0.1.1071"
---

# Extract Utility


Veeam Backup & Replication comes with an extract utility that can be used to recover machines from backup files. The extract utility does not require any interaction with Veeam Backup & Replication and can be used as an independent tool on Linux and Microsoft Windows machines.

The extract utility can be helpful, for example, if it is written to the tape next to machine backup files. In this case, you get a possibility to recover machines from backups at any moment of time even if backups are removed from Veeam Backup & Replication or Veeam Backup & Replication is not installed.

|  |
| --- |
| Important |
| If you want to use the extract utility to work with backup files located on any of the extents of your scale-out backup repository, make sure that incremental and full backup files are located on the same extent. |

The extract utility can be used in two interfaces:

* Graphic user interface (GUI).
* Command-line interface working in the [interactive](extract_utility_interactive_mode.md) and [regular mode](extract_utility_console.md).

The extract utility is located in the installation folder of Veeam Backup & Replication, by default: %PROGRAMFILES%\Veeam\Backup and Replication\Backup. The folder contains several files for the extract utility:

* Veeam.Backup.Extractor.exe — utility working in GUI (can be used on Microsoft Windows machines only).
* extract.exe — utility working in the command-line interface, a version for Microsoft Windows.
* extract — utility working in the command-line interface, a version for Linux.

You can also separately download the extract utility from [Veeam website](https://www.veeam.com/backup-replication-vcp-download.html?tab=extensions). It requires a registered Veeam account.

Related Topics

* [Using the Extract Utility using the GUI](extract_utility_gui.md)
* [Using the extract utility in the interactive mode](extract_utility_interactive_mode.md)
* [Using the extract utility from the command line](extract_utility_console.md)


