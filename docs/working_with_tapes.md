---
title: "Tapes"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/working_with_tapes.html"
last_updated: "4/16/2025"
product_version: "13.0.1.1071"
---

# Tapes


All tapes managed by Veeam Backup & Replication belong to one of the media pools. Generally, the new tapes are in the Free media pool. Tapes that were written by tape jobs stay in the media pools that are targets to these tape jobs.

If you offload tapes from your tape device, their status changes to Offline, but they stay visible in the console.

Tape media in Veeam Backup & Replication are displayed in the Tape Infrastructure view, either under the Media Pools or under the Libraries > LibraryName node > Media. You can work with both online and offline tapes:

* Tapes that are currently loaded to the tape device are available under the Online node.
* Tapes that have been unloaded from the tape device are shown under the Offline node.

|  |
| --- |
| Note |
| Before you start to use tapes loaded into the mail slot and tapes recently created in the virtual tape library (VTL), import them. To do that, open the Tape Infrastructure view, in the inventory pane click the Libraries node, select the required library, right-click it and select Import tapes. |

All tapes are grouped to service or user-created media pools available under the Tape Infrastructure > Media Pools node. You can also view tapes under the Tape Infrastructure > Libraries > LibraryName node > Media.

Veeam Backup & Replication can use only online tapes for backup to tape and file to tape jobs.

* If the tape you have inserted is registered in the Veeam backup database and the current media set can still be used, Veeam Backup & Replication will continue writing to this media set and append the new content to the content recently written on the tape.
* If the tape you have inserted is not registered in the Veeam backup database, it will be processed according to the following algorithm:

+ A new empty tape will be placed to the Free media pool and used for writing data.
+ A tape containing any data written on another Veeam backup server or with another tape backup solution will be placed to the Unrecognized media pool. You need to catalog such tapes.

Related Topics

* [Managing Tapes](managing_tapes.md)
* [Tape Protection](tape_protection.md)
* [Tape Data Retention](tape_data_retention.md)
* [Tape Encryption](encryption_tape.md)
* [Tape Alerts](tape_alert.md)
* [WORM Tapes](worm_tapes.md)


