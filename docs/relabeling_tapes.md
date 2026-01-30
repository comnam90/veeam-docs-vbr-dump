---
title: "Relabeling Tapes"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/relabeling_tapes.html"
last_updated: "8/25/2023"
product_version: "13.0.1.1071"
---

# Relabeling Tapes


To change a barcode label on a tape, you must correctly perform tape relabeling. To do that:

1. Physically remove the tape from the library.
2. From the Veeam Backup & Replication console, rescan the library, as described in section [Rescanning Tape Devices](rescan_tape_library.md). Alternatively, you can wait for 3 minutes for the scheduled rescan to run.

After the library rescan, the tape becomes offline. That is indicated by a black and white icon for this tape.

1. Remove the tape from Veeam Backup & Replication, as described in section [Removing Tapes from Catalog](removing_tapes_from_catalog.md).
2. Physically change the label on the tape.
3. Insert the tape into the IO slot or into the tape library magazine and give the library a minute to discover the changes.
4. Import the tapes or rescan the library:

* If you loaded the tapes into the IO slot, import the tapes. To do this, open the Tape Infrastructure view, expand the Libraries node and select the library into which you have loaded the tapes. Click Import Tapes on the ribbon. Alternatively, you can right-click the necessary library in the working area and select Import Tapes.
* If you loaded tapes into the tape library magazine, rescan the tape library. To do this, click Rescan Library on the ribbon. Alternatively, you can right-click the necessary library in the working area and select Rescan library.

1. [Optionally] If you need data written to the inserted tape, catalog the appeared tape.


