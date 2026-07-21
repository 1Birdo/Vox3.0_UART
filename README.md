<div align="center">

# Vodafone Vox 3.0 UART Research

<img src="https://github.com/user-attachments/assets/9c058053-3b5b-4f54-aab5-71c49105aeed" alt="Vodafone Vox 3.0" width="220">

### Universal Asynchronous Receiver–Transmitter (UART)

**Current Status**

UART access has been successfully established. The serial console is accessible, however the secure boot chain and firmware remain protected. No publicly known vulnerabilities or practical software attack vectors have been identified on current firmware.

</div>

---

## Summary

```text
UART Access        ✓ Available
Bootloader         Protected
Shell              Restricted BusyBox
Privilege Escalation  Not Achieved
Current Focus      NAND Firmware Extraction
```

---

## UART Configuration

| Parameter    | Value      |
| ------------ | ---------- |
| Baud Rate    | **115200** |
| Data Bits    | **8**      |
| Stop Bits    | **1**      |
| Parity       | **None**   |
| Flow Control | **None**   |

---

## Current Findings

Following extensive testing of both the **Sercomm SHG3000** and **Technicolor THG3000** hardware variants, no practical software-based method of obtaining privileged access has been identified.

| Component               | Findings                                                                                                                                               |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Bootloader**          | Broadcom CFE protected by BTRM Secure Boot. Boot interruption is disabled and firmware signatures are enforced.                                        |
| **Firmware**            | Current ISP firmware exposes no publicly disclosed or reproducible authenticated remote code execution vulnerabilities.                                |
| **Network Services**    | Management interfaces are limited to SSH and HTTP(S). SSH requires key authentication, while the web interface implements modern security protections. |
| **UART Console**        | Accessible over 3.3V UART (115200 8N1). The console provides a restricted BusyBox shell with limited permissions.                                      |
| **Filesystem**          | System partitions are read-only. Administrative utilities such as `su` and `sudo` are unavailable.                                                     |
| **Firmware Extraction** | Full firmware acquisition remains possible through NAND flash extraction using either an SOIC-8 clip or chip removal.                                  |

---

## Research Roadmap

### Hardware Analysis

* Acquire a complete NAND flash image.
* Extract UBI, SquashFS and JFFS2 filesystems.
* Reverse engineer firmware contents.
* Identify:

  * Hidden accounts
  * Hard-coded credentials
  * Debug functionality
  * Firmware signing keys
  * Manufacturing backdoors

### Software Analysis

Software research remains ongoing and is focused on future firmware revisions.

Current objectives include:

* Monitoring Vodafone firmware releases.
* Comparing firmware revisions.
* Investigating downgrade opportunities.
* Reviewing newly disclosed vulnerabilities.

---

## Required Equipment

| Hardware                            | Purpose                     |
| ----------------------------------- | --------------------------- |
| SOIC-8 Test Clip                    | In-circuit flash extraction |
| XGecu T56 / RT809H / Bus Pirate     | NAND programmer             |
| Hot-air Rework Station *(optional)* | Chip removal                |
| Linux                               | Firmware analysis           |
| `nanddump`                          | NAND acquisition            |
| `binwalk`                           | Firmware extraction         |
| `ubireader`                         | UBI filesystem analysis     |

---

## Media

### UART Demonstration

UART communication is demonstrated below. Connection is successfully established approximately **18 seconds** into the recording after reconnecting the serial wiring.

[![UART Demonstration](https://github.com/user-attachments/assets/e0d56086-0873-4aca-a1d1-1ef9fd41966b)](https://github.com/user-attachments/assets/cb16c278-8b7d-44cb-b9e5-09e71b830c30)

### Hardware Images

<div align="center">

<img src="https://github.com/user-attachments/assets/e0d56086-0873-4aca-a1d1-1ef9fd41966b" width="45%">
<img src="https://github.com/user-attachments/assets/0e98267b-256c-4361-be9e-a0d92806d1fe" width="45%">

<img src="https://github.com/user-attachments/assets/21aac59d-8116-4d93-8dc3-fb684bb86f0b" width="45%">
<img src="https://github.com/user-attachments/assets/bb7b793b-454f-48b8-92c0-b2904dcdeab2" width="45%">

</div>

---

## Project Objectives

This repository documents the ongoing security research and reverse engineering of the Vodafone Vox 3.0 platform.

Areas of investigation include:

* UART access
* Bootloader analysis
* Secure Boot
* Firmware reverse engineering
* NAND extraction
* Filesystem analysis
* Hardware teardown
* Vulnerability research

Both successful and unsuccessful approaches are documented to provide a complete technical reference for future research.

> **Disclaimer:** This project is intended for educational purposes and authorised security research only. Perform testing only on hardware you own or have permission to analyse. Modifying ISP-provided equipment may void warranties or violate service agreements.

---

## References

* **OpenWrt Table of Hardware**
  https://openwrt.org/toh/vodafone/vodafone_power_station

* **Research Blog**
  https://blog.birdo.uk

* **Main Website**
  https://birdo.uk
