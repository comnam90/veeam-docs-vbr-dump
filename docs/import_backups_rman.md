---
title: "Importing Backup Files"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_backups_rman.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Importing Backup Files


If the Veeam Backup & Replication server has failed and you have restored it in a new location, you can copy the backup files to a new repository and re-map the Veeam Plug-In backup files.

Limitations and Prerequisites

Consider the following limitations:

* If backup files are not imported according to instructions given in this section, Veeam Plug-In backup and restore operations may fail.
* The repository from which you plan to import backups must be added to the Veeam Backup & Replication infrastructure. Otherwise you will not be able to access backup files.

* [For imports to the scale-out backup repository] Before importing your backup, consider that the names of all backup files (.VAB, .VASM, .VACM) and paths to these files contain only the following allowed characters:

* a-zA-Z0-9
* \_-.+=@^

If your backup was initially created on a standalone backup server, the default name of the backup metadata file (.VACM) contains forbidden characters. Before importing, you must delete forbidden characters from the file name or replace them with the allowed characters.

Importing Veeam Plug-In Backup Files

To import Veeam Plug-In backup files, do the following:

1. Move the folder with the backup file to the required backup repository or create a new backup repository with this folder as a subfolder.

|  |
| --- |
| Important |
| Make sure that you import backup files and all related metadata files. Each backup folder includes a Veeam Plug-In backup file (.VAB) with its own storage metadata file (.VASM), and a single backup job metadata file (.VACM).  You can perform the import operation even in case of a missing .VACM file. |

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. In the inventory pane of the Backup Infrastructure view, select the Backup Repositories node.
3. In the working area, select the required backup repository and click Rescan on the ribbon. Alternatively, you can right-click the backup repository and select Rescan.

During the rescan operation, Veeam Backup & Replication gathers information about backups that are currently available in the backup repository and updates the list of backups in the configuration database. After the rescan operation, backups that were not in this configuration database will be shown on the Home view in the Backups > Disk (Imported) node. In certain cases, the backups can be displayed in other nodes:

* In case of capacity tier, the backups are displayed under the Backups > Capacity Tier (Imported) node in the inventory pane.
* In case of object storage, the backups are displayed under the Backups > Object Storage (Imported) node in the inventory pane.

[![Rescan Backup Repository](images/plugins_repo_rescan.webp)](images/plugins_repo_rescan.webp "Rescan Backup Repository")

1. On the Oracle server, use the terminal to set the new repository as a target in the Veeam Plug-In settings:

* For Windows:

|  |
| --- |
| "%PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\OracleRMANConfigTool" --set-repositories  Available backup repositories: |

* For Linux and Unix:

|  |
| --- |
| OracleRMANConfigTool --set-repositories  Available backup repositories: 1. serv55.tech.local 2. serv07\_repo Enter repository number: 1 |

1. Start the Veeam Plug-In configuration tool with the --map-backup parameter to re-map the plug-in backups:

|  |
| --- |
| Note |
| After you import the backup, map the imported backup to continue to back up to this repository. Using the Veeam Plug-In configuration tools, select the new repository as the target. |

* For Windows:

|  |
| --- |
| "%PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\OracleRMANConfigTool" --map-backup |

* For Linux and Unix:

|  |
| --- |
| OracleRMANConfigTool --map-backup |


