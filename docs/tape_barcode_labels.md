---
title: "Tape Barcode Labels"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_barcode_labels.html"
last_updated: "6/25/2026"
product_version: "13.0.2.29"
---

# Tape Barcode Labels


Library tapes can be marked with barcode labels that simplify identification of tapes and their types. Although the main source of information about the tape for Veeam Backup & Replication is a cartridge memory chip (LTO-CM), it can be read only when the media is inserted into the drive. Thus, correct labeling of tapes turns very useful for management of tape media.

Each barcode label used for marking LTO tapes supported by Veeam Backup & Replication consists of eight characters: a six-character volume serial ID and a two-character media ID. The media ID defines the tape type. The labels use the uppercase letters A through Z and the numbers 0 through 9, for example: ABC123L8, where ABC123 is the volume serial ID, L8 is the media ID indicating LTO of generation 8.

LTO data tapes used in devices supported by Veeam Backup & Replication may have the following media ID:

Tape Barcode Labels

| Media ID | Description |
| L3 | Generation 3 |
| L4 | Generation 4 |
| L5 | Generation 5 |
| L6 | Generation 6 |
| L7 | Generation 7 |
| L8 | Generation 8 |
| L9 | Generation 9 |
| LA | Generation 10 |
| LT | Generation 3 WORM |
| LU | Generation 4 WORM |
| LV | Generation 5 WORM |
| LW | Generation 6 WORM |
| LX | Generation 7 WORM |
| LY | Generation 8 WORM |
| LZ | Generation 9 WORM |
| LH | Generation 10 WORM |
| CU | Universal cleaning |

|  |
| --- |
| Important |
| Consider the following:   * If you have multiple libraries, ensure that the barcodes are unique throughout the infrastructure. * If tapes have incorrect barcode labels, for example, labels on ordinary (non-WORM) tapes indicate that they are of WORM or cleaning type, Veeam Backup & Replication may incorrectly identify such tapes. |

Cleaning and diagnostic tapes use unique labels to distinguish them from data tapes. The first three alphanumeric characters in the volume ID indicate the tape type:

* Cleaning tapes use the CLNxxx or CLRxxx prefixes as the cleaning tape identifier plus the cleaning media ID, for example: CLNU01CU, where CLNU01 is the cleaning media ID, CU is the universal indicator of the cleaning media.

Veeam Backup & Replication recognizes cleaning tapes by the CLNxxx or CLRxxx barcode prefixes, as the cleaning media ID may differ depending on the drive and tape manufacturer. For HP tape libraries, the cleaning tape identifier for LTO is L1 for the Ultrium universal cleaning cartridge used in LTO1, LTO2 and LTO3 drives, for example: CLNH99L1.

|  |
| --- |
| Note |
| In addition to the barcode label identification, Veeam Backup & Replication can use the following methods to identify cleaning tapes:   * Reading tape drive alerts — if the drive sends an alert indicating it is a cleaning tape, the tape is marked accordingly. * Reading SCSI medium chips — Veeam Backup & Replication reads the tape's chip to see if it is a cleaning tape or not. * Any tape from the library's dedicated cleaner slot is considered a cleaning one. |

* Diagnostic tapes use DG[space]xxx as diagnostic tape serial ID plus the media ID, for example: DG 001L8, where DG 001 is the diagnostic tape serial ID, L8 is the media ID.


