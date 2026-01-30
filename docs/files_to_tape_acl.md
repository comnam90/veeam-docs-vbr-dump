---
title: "ACL Handling Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/files_to_tape_acl.html"
last_updated: "5/29/2023"
product_version: "13.0.1.1071"
---

# ACL Handling Settings


To specify how the file to tape job will process permissions and attributes:

1. At the Options step of the wizard, click Advanced.
2. On the ACL Handling tab, define the settings:

* Select Folder-level only (recommended) to back up permissions and attributes from folders only. The restored files will inherit permissions from the target folder.
* Select Files and folders (slower) to back up permissions and attributes from both folders and individual files. This option can significantly reduce the backup performance.

![ACL Handling Settings](images/files_to_tape_advanced_acl.webp)


