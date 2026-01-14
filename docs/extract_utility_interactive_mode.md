---
title: "Using Extract Utility in Interactive Mode"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/extract_utility_interactive_mode.html"
last_updated: "2/20/2025"
product_version: "13.0.1.1071"
---

# Using Extract Utility in Interactive Mode

In this article

To start the extract utility in the interactive mode, run the extract.exe file from the product installation folder (in case of a Linux machine, run the extract file).

You will have to sequentially enter the following arguments:

1. A path to the backup file from which the machine must be restored. After you enter the path, the extract utility will display a list of all machines included in the backup and their description.
2. A name of the machine that you want to restore. If there is more than one machine with the specified name in the backup, you will be asked to specify the host on which the backed-up machine resides. If you want to restore all machines from the backup, press [Enter] on the keyboard.
3. If the backup was encrypted, password that was used to encrypt the backup file.
4. An output directory to which machines must be restored. If you want to restore machines to the current directory, press [Enter] on the keyboard.
5. The operation confirmation. Press [Y] on the keyboard to restore a machine to the directory you specified. If you want to abort the operation, press [Enter] on the keyboard.

Page updated 2/20/2025

Page content applies to build 13.0.1.1071
