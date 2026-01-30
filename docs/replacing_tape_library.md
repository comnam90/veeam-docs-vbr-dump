---
title: "Replacing Tape Devices"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replacing_tape_library.html"
last_updated: "10/24/2025"
product_version: "13.0.1.1071"
---

# Replacing Tape Devices


You may want to stop using a tape library or a standalone tape drive, for example, because of breakdown or low efficiency, and replace it with a new tape device. To replace the device seamlessly and continue using the tapes within the same media pool, follow the instructions below.

|  |
| --- |
| Note |
| Moving tapes with barcodes between libraries requires additional steps. For more information, see [Moving Tapes with Barcodes Between Libraries](import_tapes_this_server.md#barcodes). |

To replace a tape device:

1. Connect the new tape device to the tape server. For more information, see [Connecting Tape Devices](connecting_tape_devices.md).
2. Add the tape device to the media pool to which the old tape device was added. Open the media pool settings and go to the Tapes step of the wizard. For more information, see [Modifying Media Pools](modifying_media_pools.md). If the old tape device was added to several media pools, add the new tape device to the same media pools.
3. Remove the old tape device from the media pools. To do that, click Manage, select the tape, click Remove. If the old tape device was added to several media pools, remove the tape device from all of these media pools.
4. Disconnect the old tape device from the tape server.
5. Remove the old tape device from Veeam Backup & Replication. For more information, see [Removing Tape Devices](removing_tape_libraries.md).
6. Make sure that you do not remove the offline tapes from Veeam Backup & Replication.
7. Offload the tapes from the old tape device and load them to the new tape device.
8. Rescan the tape device.

To replace a standalone tape drive:

1. Offload the tape from the old standalone tape drive if it was loaded.
2. Add a new standalone tape drive.
3. Disconnect the old tape drive.
4. Add the tape device to the media pool to which the old tape device was added. Open the media pool settings and go to the Tapes step of the wizard. For more information, see [Modifying Media Pools](modifying_media_pools.md). If the old tape device was added to several media pools, add the new tape device to the same media pools.
5. Remove the old tape device from the media pools. For more information, see [Removing Tape Devices](removing_tape_libraries.md).

Veeam Backup & Replication prompts to select a new tape drive.

1. Select the new tape drive.

The tapes in the media pool will now be associated with the new tape drive.

1. Repeat the procedure for each media pool where the old tape drive was used.

As a result, the tapes remain in the same media pools and the data is intact.


