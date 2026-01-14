---
title: "Tape Drive Alerts"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_alerts.html"
last_updated: "5/20/2025"
product_version: "13.0.1.1071"
---

# Tape Drive Alerts

In this article

There are 3 types of error flags:

| Severity | Urgent User Intervention | Risk of Data Loss | Explanations |
| --- | --- | --- | --- |
| Critical | X | X |  |
| Warning |  | X | X |
| Information |  |  | X |

You may get one of the following tape drive alerts when working with Veeam Backup & Replication:

| Alert Code (Dec) | Alert Code (Hex) | Flag | Severity | Description | Cause |
| --- | --- | --- | --- | --- | --- |
| 1 | 0x01 | Read warning | Warning | The tape drive is having problems reading data. No data has been lost, but there has been a reduction in the performance of the tape. | The drive is having severe trouble reading. |
| 2 | 0x02 | Write warning | Warning | The tape drive is having problems writing data. No data has been lost, but there has been a reduction in the capacity of the tape. | The drive is having severe trouble writing. |
| 3 | 0x03 | Hard error | Warning | The operation has stopped because an error has occurred while reading or writing data that the drive cannot correct. | The drive had a hard read or write error. |
| 4 | 0x04 | Media error | Critical | Your data is at risk:   1. Copy any data you require from this tape. 2. Do not use this tape again. 3. Restart the operation with a different tape. | Media can no longer be written/read, or performance is severely degraded. |
| 5 | 0x05 | Read failure | Critical | The tape is damaged or the drive is faulty. Call the tape drive supplier helpline. | The drive can no longer read data from the tape. |
| 6 | 0x06 | Write failure | Critical | The tape is from a faulty batch or the tape drive is faulty:   1. Use a good tape to test the drive. 2. If problem persists, call the tape drive supplier helpline. | The drive can no longer write data to the tape. |
| 7 | 0x07 | Media life | Warning | The tape cartridge has reached the end of its calculated useful life:   1. Copy data you need to another tape. 2. Discard the old tape. | The media has exceeded its specified life. |
| 8 | 0x08 | Not data grade tape | Warning | The tape cartridge is not data-grade. Any data you back up to the tape are at risk. Replace the cartridge with a data-grade tape. | The drive has not been able to read the MRS stripes. |
| 9 | 0x09 | Attempted backup to write-protected tape | Critical | You are trying to write to a write-protected cartridge. Remove the write-protection or use another tape. | Write command is attempted to a write protected tape. |
| 10 | 0x0a | Tape drive is in use | Information | You cannot eject the cartridge because the tape drive is in use. Wait until the operation is complete before ejecting the cartridge. | Manual or s/w unload attempted when prevent media removal on. |
| 11 | 0x0b | Attempted backup/restore to cleaning tape | Information | The tape in the drive is a cleaning cartridge. | Cleaning tape is loaded into drive. |
| 12 | 0x0c | Unsupported cartridge type | Information | You have tried to load a cartridge of a type which is not supported by this drive. | Attempted loaded of unsupported tape format, for example, DDS2 in DDS1 drive. |
| 13 | 0x0d | Detected snapped tape | Critical | The operation has failed because the tape in the drive has experienced a mechanical failure:   1. Discard the old tape. 2. Restart the operation with a different tape. | Tape snapped/cut in the drive where media can be ejected. |
| 14 | 0x0e | Detected snapped tape | Critical | The operation has failed because the tape in the drive has experienced a mechanical failure:   1. Do not attempt to extract the tape cartridge. 2. Call the tape drive supplier helpline. | Tape snapped/cut in the drive where media cannot be ejected. |
| 15 | 0x0f | Cartridge memory chip failure | Warning | The memory in the tape cartridge has failed, which reduces performance. Do not use the cartridge for further write operations. | Memory chip failed in cartridge. |
| 16 | 0x10 | Forced eject | Critical | The operation has failed because the tape cartridge was manually de-mounted while the tape drive was actively writing or reading. | Manual or forced eject while drive actively writing or reading. |
| 17 | 0x11 | Read-only format | Warning | You have loaded a cartridge of a type that is read-only in this drive. The cartridge will appear as write-protected. | Media loaded that is read-only format. |
| 18 | 0x12 | Tape directory corrupted in the cartridge memory | Warning | The tape directory on the tape cartridge has been corrupted. File search performance will be degraded. The tape directory can be rebuilt by reading all the data on the cartridge. | Tape drive powered down with tape loaded, or permanent error prevented the tape directory being updated. |
| 19 | 0x13 | Nearing media life | Information | The tape cartridge is nearing the end of its calculated life. It is recommended that you:   1. Use another tape cartridge for your next backup. 2. Store this tape in a safe place in case you need to restore data from it. | Media may have exceeded its specified number of passes. |
| 20 | 0x14 | Clean now | Critical | The tape drive needs cleaning:   1. If the operation has stopped, eject the tape and clean the drive. 2. If the operation has not stopped, wait for it to finish and then clean the drive.   Check the tape drive user’s manual for device specific cleaning instructions. | The drive thinks it has a head clog, or needs cleaning. |
| 21 | 0x15 | Clean periodic | Warning | The tape drive is due for routine cleaning:   1. Wait for the current operation to finish. 2. Then use a cleaning cartridge.   Check the tape drive user’s manual for device specific cleaning instructions. | The drive is ready for a periodic clean. |
| 22 | 0x16 | Expired cleaning media | Critical | The last cleaning cartridge used in the tape drive has worn out:   1. Discard the worn out cleaning cartridge. 2. Wait for the current operation to finish. 3. Then use a new cleaning cartridge. | The cleaning tape has expired. |
| 23 | 0x17 | Invalid cleaning cartridge | Critical | The last cleaning cartridge used in the tape drive was an invalid type:   1. Do not use this cleaning cartridge in this drive. 2. Wait for the current operation to finish. 3. Then use a new cleaning cartridge. | Invalid cleaning tape type used. |
| 24 | 0x18 | Request retention | Warning | The tape drive has requested a retention operation. | The drive is having severe trouble reading or writing, which will be resolved by a retention cycle. |
| 25 | 0x19 | Dual-port interface error | Warning | A redundant interface port on the tape drive has failed. | Failure of one interface port in a dual-port configuration, for example, Fibrechannel. |
| 26 | 0x1a | Cooling fan failure | Warning | A tape drive cooling fan has failed. | Fan failure inside tape drive mechanism or tape drive enclosure. |
| 27 | 0x1b | Power supply | Warning | A redundant power supply has failed inside the tape drive enclosure. Check the enclosure user’s manual for instructions on replacing the failed power supply. | Redundant PSU failure inside the tape drive enclosure or rack subsystem. |
| 28 | 0x1c | Power consumption is outside the specified range | Warning | The tape drive power consumption is outside the specified range. | Power consumption of the tape drive is outside specified range. |
| 29 | 0x1d | Preventative maintenance is required | Warning | Preventive maintenance of the tape drive is required. Check the tape drive user’s manual for device specific preventive maintenance tasks or call the tape drive supplier helpline. | The drive requires preventative maintenance (not cleaning). |
| 30 | 0x1e | Drive hardware fault | Critical | The tape drive has a hardware fault:   1. Eject the tape or magazine. 2. Reset the drive. 3. Restart the operation. | The drive has a hardware fault that requires reset to recover. |
| 31 | 0x1f | Drive hardware fault | Critical | The tape drive has a hardware fault:   1. Turn the tape drive off and then on again. 2. Restart the operation. 3. If the problem persists, call the tape drive supplier helpline. | The drive has a hardware fault which is not read/write related or requires a power cycle to recover. |
| 32 | 0x20 | Host interface fault | Warning | The tape drive has a problem with the application client interface:   1. Check the cables and cable connections. 2. Restart the operation. | The drive has identified an interfacing fault. |
| 33 | 0x21 | Eject media request | Critical | The operation has failed:   1. Eject the tape or magazine. 2. Insert the tape or magazine again. 3. Restart the operation. | Error recovery action. |
| 34 | 0x22 | Firmware download fault | Warning | The firmware download has failed because you have tried to use the incorrect firmware for this tape drive. Obtain the correct firmware and try again. | Firmware download failed. |
| 35 | 0x23 | Humidity specification exceeded | Warning | Environmental conditions inside the tape drive are outside the specified humidity range. | Drive humidity limits exceeded. |
| 36 | 0x24 | Temperature specification exceeded | Warning | Environmental conditions inside the tape drive are outside the specified temperature range. | Drive temperature limits exceeded. |
| 37 | 0x25 | Voltage specification exceeded | Warning | The voltage supply to the tape drive is outside the specified range. | Drive voltage limits exceeded. |
| 38 | 0x26 | Tape device predicted to fail | Critical | A hardware failure of the tape drive is predicted. Call the tape drive supplier helpline. | Predictive failure of drive hardware. |
| 39 | 0x27 | Drive hardware fault | Warning | The tape drive may have a hardware fault. Run extended diagnostics to verify and diagnose the problem. Check the tape drive user’s manual for device specific instructions on running extended diagnostic tests. | The drive may have had a failure which may be identified by stored diagnostic information or by running extended diagnostics (for example, Send Diagnostic). |
| 40 | 0x28 | Autoloader communication fault | Critical | The changer mechanism is having difficulty communicating with the tape drive:   1. Turn the autoloader off then on. 2. Restart the operation. 3. If problem persists, call the tape drive supplier helpline. | Loader mechanism is having trouble communicating with the tape drive. |
| 41 | 0x29 | Detected stray tape in autoloader | Critical | A tape has been left in the autoloader by a previous hardware fault:   1. Insert an empty magazine to clear the fault. 2. If the fault does not clear, turn the autoloader off and then on again. 3. If the problem persists, call the tape drive supplier helpline. | Stray tape left in loader after previous error recovery. |
| 42 | 0x2a | Autoloader mechanism fault | Warning | There is a problem with the autoloader mechanism. | Loader mechanism has a hardware fault. |
| 43 | 0x2b | Autoloader door open | Critical | The operation has failed because the autoloader door is open:   1. Clear any obstructions from the autoloader door. 2. Eject the magazine and then insert it again. 3. If the fault does not clear, turn the autoloader off and then on again. 4. If the problem persists, call the tape drive supplier helpline. | Tape changer door open. |
| 44 | 0x2c | Autoloader hardware fault | Critical | The autoloader has a hardware fault:   1. Turn the autoloader off and then on again. 2. Restart the operation. 3. If the problem persists, call the tape drive supplier helpline.   Check the autoloader user’s manual for device specific instructions on turning the device power on and off. | The loader mechanism has a hardware fault that is not mechanically related. |
| 45 | 0x2d | Autoloader cannot operate without magazine | Critical | The autoloader cannot operate without the magazine:   1. Insert the magazine into the autoloader. 2. Restart the operation. | Loader magazine not present. |
| 46 | 0x2e | Autoloader predicted to fail | Warning | A hardware failure of the changer mechanism is predicted. Call the tape drive supplier helpline. | Predictive failure of loader mechanism hardware. |
| 47 – 49 | 0x2f – 0x31 |  |  | These codes are reserved for future use. |  |
| 50 | 0x32 | Media statistics is lost | Warning | Media statistics have been lost at some time in the past. | Drive or library powered down with tape loaded. |
| 51 | 0x33 | Tape directory is corrupted | Warning | The tape directory on the tape cartridge just unloaded has been corrupted. File search performance will be degraded. The tape directory can be rebuilt by reading all the data. | Error prevented the tape directory being updated on unload. |
| 52 | 0x34 | Tape system area write failure | Critical | The tape just unloaded could not write its system area successfully:   1. Copy data to another tape cartridge. 2. Discard the old cartridge. | Write errors while writing the system log on unload. |
| 53 | 0x35 | Tape system area read failure | Critical | The tape system are could not be read successfully at load time:   1. Copy data to another tape cartridge. 2. Discard the old cartridge. | Read errors while reading the system area on load. |
| 54 | 0x36 | Start of data not found | Critical | The start or data could not be found on the tape:   1. Check you are using the correct format tape. 2. Discard the tape or return the tape to your supplier. | Tape damaged, bulk erased, or incorrect format. |
| 55 | 0x37 | Load failure | Critical | The operation has failed because the media cannot be loaded and threaded:   1. Remove the cartridge, inspect it as specified in the product manual, and retry the operation. 2. If the problem persists, call the tape drive supplier help line. | Media could not be loaded/threaded. |
| 56 | 0x38 | Medium unload failure | Critical | The operation has failed because the medium cannot be unloaded:   1. Do not attempt to extract the tape cartridge. 2. Call the tape driver supplier help line. | Unrecoverable unload failed. |
| 57 | 0x39 | Interface failure | Critical | The tape drive has a problem with the automation interface:   1. Check the power to the automation system. 2. Check the cables and cable connections. 3. Call the supplier help line if problem persists. | Automation interface failure. |
| 58 | 0x3a | Firmware failure | Warning | The tape drive has reset itself due to a detected firmware fault. If problem persists, call the supplier help line. | Firmware failure. |

Page updated 5/20/2025

Page content applies to build 13.0.1.1071
