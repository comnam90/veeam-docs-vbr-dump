---
title: "Tape Changer Alerts"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_changer_alerts.html"
last_updated: "5/20/2025"
product_version: "13.0.1.1071"
---

# Tape Changer Alerts

In this article

There are 3 types of error flags:

| Severity | Urgent User Intervention | Risk of Data Loss | Explanations |
| --- | --- | --- | --- |
| Critical | X | X |  |
| Warning |  | X | X |
| Information |  |  | X |

You may get one of the following tape changer alerts when working with Veeam Backup & Replication:

| Alert Code (Dec) | Alert Code (Hex) | Flag | Severity | Description | Cause |
| --- | --- | --- | --- | --- | --- |
| 0 | 0x00 |  | Information | Unknown changer alert. |  |
| 1 | 0x01 | Library Hardware A | Critical | The library mechanism is having difficulty communicating with the drive:   1. Turn the library off then on. 2. Restart the operation. 3. If the problem persists, call the library supplier help line. | Changer mechanism is having trouble communicating with the internal drive. |
| 2 | 0x02 | Library Hardware B | Warning | There is a problem with the library mechanism.  If problem persists call the library supplier help line. | Changer mechanism has a hardware fault. |
| 3 | 0x03 | Library Hardware C | Critical | The library has a hardware fault:   1. Reset the library. 2. Restart the operation. 3. Check the library users manual for device specific instructions on resetting the device. | The changer mechanism has a hardware fault that requires reset to recover. |
| 4 | 0x04 | Library Hardware D | Critical | The library has a hardware fault:   1. Turn the library off then on again. 2. Restart the operation. 3. If the problem persists, call the library supplier help line. 4. Check the library users manual for device specific instructions on turning the device power on and off. | The changer mechanism has a hardware fault that is not mechanically related, or requires a power cycle to recover. |
| 5 | 0x05 | Library Diagnostics Required | Warning | The library mechanism may have a hardware fault:   1. Run extended diagnostics to verify and diagnose the problem. 2. Check the library users manual for device specific instructions on running extended diagnostic tests. | The changer mechanism may a hardware fault which can be identified by extended diagnostics (for example, SCSI Send Diagnostic). |
| 6 | 0x06 | Library Interface | Critical | The library has a problem with the host interface:   1. Check the cables and connections. 2. Restart the operation. | The library has identified an interfacing fault. |
| 7 | 0x07 | Predictive Failure | Warning | A hardware failure of the library is predicted.  Call the library supplier help line. | Predictive failure of library hardware. |
| 8 | 0x08 | Library Maintenance | Warning | Preventive maintenance of the library is required.  Check the library users manual for device specific preventative maintenance tasks, or call your library supplier help line. | Library preventative maintenance required. |
| 9 | 0x09 | Library Humidity Limits | Critical | General environmental conditions inside the library are outside the specified humidity range. | Library humidity limits exceeded. |
| 10 | 0x0a | Library Temperature Limits | Critical | General environmental conditions inside the library are outside the specified temperature range. | Library temperature limits exceeded. |
| 11 | 0x0b | Library Voltage Limits | Critical | The voltage supply to the library is outside the specified range. There is a potential problem with the power supply or failure of a redundant power supply. | Library voltage limits exceeded |
| 12 | 0x0c | Library Stray Tape | Critical | A cartridge has been left inside the library by a previous hardware fault:   1. Insert an empty magazine to clear the fault. 2. If the fault does not clear, turn the library off and then on again. 3. If the problem persists, call the library supplier help line. | Stray cartridge left in library drive after previous error recovery. |
| 13 | 0x0d | Library Pick Retry | Warning | There is a potential problem with the drive ejecting cartridges or with the library mechanism picking a cartridge from a slot.  No action needs to be taken at this time.  If the problem persists, call the library supplier help line. | Operation to pick a cartridge from a slot had to perform an excessive number of retries before succeeding. |
| 14 | 0x0e | Library Place Retry | Warning | There is a potential problem with the library mechanism placing a cartridge into a slot.  No action needs to be taken at this time.  If the problem persists, call the library supplier help line. | Operation to place a cartridge into a slot had to perform an excessive number of retries before succeeding. |
| 15 | 0x0f | Library Load Retry | Warning | There is a potential problem with the drive or the library mechanism loading cartridges, or an incompatible cartridge. | Operation to load a cartridge into a drive had to perform an excessive number of retries before succeeding. |
| 16 | 0x10 | Library Door | Critical | The library has failed because the door is open:   1. Clear any obstructions from the library door. 2. Close the library door. 3. If the problem persists, call the library supplier help line. | Changer door open prevents library functioning. |
| 17 | 0x11 | Library Mailslot | Critical | There is a mechanical problem with the library media import/export mailslot. | Mechanical problem with import/export mailslot |
| 18 | 0x12 | Library Magazine | Critical | The library cannot operate without the magazine:   1. Insert the magazine into the library. 2. Restart the operation. | Library magazine not present. |
| 19 | 0x13 | Library Security | Warning | Library security has been compromised. | Library door opened then closed during operation. |
| 20 | 0x14 | Library Security Mode | Information | The library security mode has been changed. The library has either been put into secure mode, or the library has exited the secure mode.  This is for information purposes only. No action is required. | Library security mode changed. |
| 21 | 0x15 | Library Offline | Information | The library has been manually turned offline and is unavailable for use. | Library manually turned offline. |
| 22 | 0x16 | Library Drive Offline | Information | A drive inside the library has been taken offline.  This is for information purposes only. No action is required. | Library turned internal drive offline. |
| 23 | 0x17 | Library Scan Retry | Warning | There is a potential problem with the bar code label or the scanner hardware in the library mechanism.  No action needs to be taken at this time.  If the problem persists, call the library supplier help line. | Operation to scan the barcode on a cartridge had to perform an excessive number of retries before succeeding. |
| 24 | 0x18 | Library Inventory | Critical | The library has detected an inconsistency in its inventory.   1. Redo the library inventory to correct inconsistency. 2. Restart the operation. 3. Check the applications users manual or the hardware users manual for specific instructions on redoing the library inventory. | Inconsistent media inventory. |
| 25 | 0x19 | Library Illegal Operation | Warning | A library operation has been attempted that is invalid at this time. | Illegal operation detected. |
| 26 | 0x1a | Dual-Port Interface Error | Warning | A redundant interface port on the library has failed. | Failure of one interface port in a dual-port configuration, for example, Fibrechannel. |
| 27 | 0x1b | Cooling Fan Failure | Warning | A library cooling fan has failed. | One or more fans inside the library have failed. Internal flag state only cleared when all fans are working again. |
| 28 | 0x1c | Power Supply | Warning | A redundant power supply has failed inside the library.  Check the library users manual for instructions on replacing the failed power supply. | Redundant PSU failure inside the library subsystem. |
| 29 | 0x1d | Power Consumption | Warning | The library power consumption is outside the specified range. | Power consumption of one or more devices inside the library is outside specified range. |
| 30 | 0x1e | Pass-through mechanism  failure. | Critical | A failure has occurred in the cartridge pass-through mechanism between two library modules. | Error occurred in pass-through mechanism during self test or while attempting to transfer a cartridge between library modules. |
| 31 | 0x1f | Cartridge in pass-through mechanism | Critical | A cartridge has been left in the pass-through mechanism from a previous hardware fault.  Check the library users guide for instructions on clearing this fault. | Cartridge left in the pass-through  mechanism between two library modules. |
| 32 | 0x20 | Unreadable bar code labels | Information | The library was unable to read the bar code on a cartridge. | Unable to read a barcode label on a cartridge during library inventory/scan. |

Page updated 5/20/2025

Page content applies to build 13.0.1.1071
