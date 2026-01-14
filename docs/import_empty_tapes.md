---
title: "Loading Empty Tapes"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_empty_tapes.html"
last_updated: "8/8/2024"
product_version: "13.0.1.1071"
---

# Loading Empty Tapes

In this article

To load empty tapes, perform the following steps:

1. Load the tapes into the mail slot or directly into the tape library magazine.
2. If you loaded the tapes to the mail slot, import the tapes. To do this, open the Tape Infrastructure view, expand the Libraries node and select the library to which you have loaded the tapes. Click Import Tapes on the ribbon. You can also right-click the necessary library in the working area and select Import Tapes.
3. If you loaded tapes into the tape library magazine, rescan the tape library. To do this, click Rescan Library on the ribbon. You can also right-click the necessary library in the working area and select Rescan library.
4. The tapes will appear in the Unrecognized media pool.
5. Right-click the tapes and select Inventory.
6. The tapes will be moved to the Free media pool.

If you want to refill the free tape resources in your tape device, you can overwrite tapes containing outdated Veeam archives. For more information, see [Loading Tapes Written on This Backup Server](import_tapes_this_server.md).

|  |
| --- |
| Tip |
| To understand which of the tapes can be overwritten, you can check their expiration date. In the Tape Infrastructure view, open the Media Pools node and select the media pool that you want to replenish. Check the Expires in field in the working area. You can sort the tapes by the expiration date and get the list of tapes that can be reused. |

Page updated 8/8/2024

Page content applies to build 13.0.1.1071
