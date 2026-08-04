---
title: "Restoring from Veeam Recovery Media Locally"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_instant_restore_media_local.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring from Veeam Recovery Media Locally


You can perform local bare metal recovery on a Veeam Agent computer using Veeam Recovery Media. To do this, you must have physical access to the computer that must be recovered:

1. Prepare Veeam Recovery Media for the computer that must be recovered:

* For a Microsoft Windows computer, create Veeam Recovery Media in the Veeam Backup & Replication interface. To learn more, see [Creating Veeam Recovery Media](recovery_media_create.md).
* For a Linux computer, download Veeam Recovery Media from the [Veeam website](https://www.veeam.com/linux-backup-download.html) or create a custom Veeam Recovery Media. To learn more, see the [Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforlinux/userguide/recovery_media.html?ver=13) section in the Veeam Agent for Linux User Guide.

1. Boot the computer that must be recovered from the Veeam Recovery Media and perform the restore locally.

The process of data restore with Veeam Recovery Media in the Veeam Agent management scenario does not differ from the same process on a computer that runs Veeam Agent operating in the standalone mode:

* For information on data restore with Veeam Recovery Media on a Microsoft Windows computer, see the [Restoring from Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforwindows/userguide/image_boot.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.
* For information on data restore with Veeam Recovery Media on a Linux computer, see the [Restoring from Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforlinux/userguide/baremetal.html?ver=13) section in the Veeam Agent for Linux User Guide.

Page updated 2026-07-21

