---
title: "Loading Tapes Written with 3rd-Party Backup Solution"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_tapes_3rd_party.html"
last_updated: "7/11/2023"
product_version: "13.0.1.1071"
---

# Loading Tapes Written with 3rd-Party Backup Solution


Veeam Backup & Replication does not support backups written with another backup solution even if they are written in the supported format.

|  |
| --- |
| Important |
| You cannot restore data written with 3rd-party tape recording solutions. |

If the tapes written with another backup solution contain valuable data, do not run any procedures against them, for example, inventory or catalog. Veeam Backup & Replication recognizes such tapes as writable and may use them for Veeam tape jobs.

If you do not need the data on these tapes, you can erase them and use for writing data with Veeam Backup & Replication.

To erase and re-use tapes containing non-Veeam data:

1. Load the tapes into the mail slot or directly into the tape library magazine.
2. If you loaded the tapes to the mail slot, import the tapes. To do this, open the Tape Infrastructure view, expand the Libraries node and select the library to which you have loaded the tapes. Click Import Tapes on the ribbon. You can also right-click the necessary library in the working area and select Import Tapes.
3. If you loaded tapes into the tape library magazine, rescan the tape library. To do this, click Rescan Library on the ribbon. You can also right-click the necessary library in the working area and select Rescan library.
4. The tapes will appear in the Unrecognized media pool.
5. Select tapes you want to erase and click Erase on the ribbon. Alternatively, you can right-click selected tapes and choose Erase. Choose Short erase and click OK. For more information, see [Erasing Tapes](erasing_tapes.md).
6. The tapes will be moved to the Free media pool.


