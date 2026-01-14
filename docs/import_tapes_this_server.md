---
title: "Loading Tapes Written on This Backup Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_tapes_this_server.html"
last_updated: "6/14/2024"
product_version: "13.0.1.1071"
---

# Loading Tapes Written on This Backup Server

In this article

If the tapes that you load were written on the same Veeam backup server, the Veeam backup database has information about them. The procedure is different for tape libraries depending on whether they support barcodes or not.

Loading Tapes with Barcodes

To load tapes with barcodes written in the same tape library:

1. Load the tapes into the mail slot or directly into the tape library magazine.
2. If you loaded the tapes to the mail slot, import the tapes. To do this, open the Tape Infrastructure view, expand the Libraries node and select the library to which you have loaded the tapes. Click Import Tapes on the ribbon. You can also right-click the necessary library in the working area and select Import tapes.
3. If you loaded tapes into the tape library magazine, rescan the tape library. To do this, click Rescan Library on the ribbon. You can also right-click the necessary library in the working area and select Rescan library.
4. Veeam Backup & Replication will automatically move the tapes to their parent media pools. You can start working with them.

Moving Tapes with Barcodes Between Libraries

We strongly recommend that you do not move tapes with barcodes written in one library to another library, as that can result in various errors and return messages about barcode duplicates.

If you cannot avoid moving tapes with barcodes between the libraries, make sure you perform all the following steps:

1. Unload the tapes from the mail slot or from the magazine of the tape library.
2. Rescan the library that you remove the tapes from. To do this, open the Tape Infrastructure view, expand the Libraries node and select the library that you remove the tapes from. Click Rescan Library on the ribbon. You can also right-click the necessary library in the working area and select Rescan library.
3. Remove the tapes from the catalog. To do this, navigate to the list of tapes either under the Media Pools node or under the Libraries > LibraryName node > Media > Offline node. Select offline tapes you want to remove from the catalog and click Remove from Catalog on the ribbon. Alternatively, you can right-click selected tapes and choose Remove from Catalog from the shortcut menu. In the opened dialog box, click Yes to confirm removal.
4. Load the tapes into the mail slot or directly into the magazine of the tape library that you move the tapes to.
5. Catalog the loaded tapes in the new library. To do this, navigate to the list of tapes either under the Media Pools node or under the Libraries > LibraryName node > Media node. Select the necessary tapes in the list and click Catalog on the ribbon. Alternatively, you can right-click the selected tapes and choose Catalog.
6. Veeam Backup & Replication adds the tapes to the new library. You can start working with them.

Loading Tapes without Barcodes

To load tapes without barcodes:

1. Load the tapes into the mail slot or directly into the tape library magazine.
2. If you loaded the tapes to the mail slot, import the tapes. To do this, open the Tape Infrastructure view, expand the Libraries node and select the library to which you have loaded the tapes. Click Import Tapes on the ribbon. You can also right-click the necessary library in the working area and select Import tapes.
3. If you loaded tapes into the tape library magazine, rescan the tape library. To do this, click Rescan Library on the ribbon. You can also right-click the necessary library in the working area and select Rescan library.
4. The tapes will appear in the Unrecognized media pool.
5. Right-click the tapes and select Inventory.
6. Veeam Backup & Replication will move the tapes to their parent media pools. You can start working with them.

Note that if the tapes are expired, they will be overwritten by tape rotation scheme set for the tapes' parent media pool.

Page updated 6/14/2024

Page content applies to build 13.0.1.1071
