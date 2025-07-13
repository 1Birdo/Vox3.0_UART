<div align="center">
  <h1>🛠️ Vox 3.0 UART Shell – Status Update</h1>
  <img src="https://github.com/user-attachments/assets/9a058053-3b5b-4f54-aab5-71c49105aeed" alt="Vox 3.0 Router" width="200">
  <h3>(Universal Asynchronous Receiver-Transmitter)</h3>
  <p><strong>Current verdict: UART shell reachable, but the bootloader & firmware are locked down. No known vulns or open services.</strong></p>
</div>

---

<h2>🖥️ Connection Settings</h2>
  
  | Setting       | Value    |
  |---------------|----------|
  | **Baud rate** | 115200   |
  | **Data bits** | 8        |
  | **Stop bits** | 1        |
  | **Parity**    | None     |
  | **Flow control** | None 

## 🚨 2025-07-14 – Reality Check

After exhaustive testing the Vodafone Vox 3.0 (Sercomm SHG3000 / Technicolor THG3000) is **not** an easy target:

| Finding | Detail |
|---|---|
| **Bootloader** | Signed & password-protected CFE (Broadcom BTRM). No `autoboot` interruption or `tftp` recovery path. |
| **Web UI** | Latest ISP firmware (Homeware for THG3000, Sercomm OEM for SHG3000) has **no authenticated RCE** disclosed or fuzzed. |
| **Network services** | Only exposed ports are 22 (SSH) and 80/443 (HTTP/S). SSH is key-only, HTTP/S is CSRF-hardened. |
| **UART console** | Accessible (115200 8N1, 3.3 V), but drops to a **restricted BusyBox shell** with non-privileged user (`admin`). No `su`, no `sudo`, no writable `/etc`. |
| **NAND dump** | Possible via **chip-off / SOIC-8 clip**. Requires hot-air or precision rework. ECC is BCH-8 (Technicolor) / BCH-4 (Sercomm). |

---

## 🎯 Revised Roadmap

1. **Hardware path (next)**  
   - SOIC-8 clip + XGecu T56 or similar → raw NAND dump.  
   - Binwalk / `ubireader_extract_images` → squashfs / jffs2 extraction.  
   - Search for hard-coded creds, backdoor accounts, or firmware signing keys.

2. **Software path (on hold)**  
   - Keep monitoring ISP firmware releases for new vulns.  
   - If a signed firmware update ever leaks, diff & hunt for downgrade attacks.

---

## 🧰 What You’ll Need Now

| Item | Purpose |
|---|---|
| SOIC-8 test clip (W25Qxx compatible) | In-circuit NAND read |
| XGecu T56, RT809H, or Bus Pirate | NAND programmer |
| Hot-air station (optional) | Chip-off if clip fails |
| Linux w/ `nanddump`, `binwalk`, `ubireader` | Analysis |

---

## 📺 Updated Media

- [Video: UART boot log (locked shell)](https://github.com/user-attachments/assets/cb16c278-8b7d-44cb-b9e5-09e71b830c30)  
- [High-res PCB shots](https://github.com/user-attachments/assets/e0d56086-0873-4aca-a1d1-1ef9fd41966b) – UART header & NAND location marked.

---

## 📖 Repository Purpose (unchanged)

Document **all** attempts—successful or not—to gain root on the Vodafone Vox 3.0 for educational / research use.

> **Reminder:** Only experiment on hardware you own. Tampering may violate ISP ToS and void warranties.

---

## 🔗 Quick Links

- [OpenWRT ToH – Vodafone Power Station](https://openwrt.org/toh/vodafone/vodafone_power_station) (still the best public reference)  
- [My Dashboard](https://dashboard.birdo.uk) – live notes when NAND dump starts.  
- [Main Site](https://birdo.uk) – other tooling & write-ups.

---

```bash
# TL;DR
# UART ✔️ reachable
# Shell ❌ locked
# Next step: chip-off NAND dump
```
