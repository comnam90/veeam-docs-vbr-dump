---
title: "Tapes Availability and Write-Protection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tapes_availability.html"
last_updated: "5/20/2025"
product_version: "13.0.1.1071"
---

# Tapes Availability and Write-Protection


Before archiving data to tape media, Veeam Backup & Replication detects available tapes in the target media pool. Unavailable tapes are filtered out and are not used for writing data. A tape may be unavailable for one of the following reasons:

* The tape cannot be used according to the retention policy set for the media pool.
* The tape is offline.
* The tape has the write-protect switch set.

If your tape is write-protected and you want to write data to this tape, you must eject the tape from the drive and drag the write protection switch off. After you insert the tape back to the drive, you must inventory the tape to mark it as writable in the Veeam Backup & Replication database.


