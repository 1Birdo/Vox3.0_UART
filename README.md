# 🛠️ Vox 3.0 UART Shell Access  
### (Universal Asynchronous Receiver-Transmitter)

Gain UART shell access on a Vodafone Vox 3.0 router

---

## 📋 Project Overview
This repository documents how to access a UART serial console on the Vodafone Vox 3.0 router, providing direct shell access to the underlying Linux system. Useful for research, debugging, or developing custom firmware.

> **⚠️ Note:** Intended for educational and personal research only. Only perform on devices you own or have explicit permission to access.

---

## 🎯 Objectives
- Gain shell access via UART interface
- Extract original firmware for analysis
- Explore potential for:
  - Installing alternative OS (OpenWRT)
  - Modifying existing firmware
  - Discovering vulnerabilities
  - Privilege escalation opportunities

> *"While unlikely that a proprietary ISP device would have vulnerabilities, it's not unheard of. Worth investigating!"*

---

## 🛠️ Required Equipment

### Hardware:
- Vodafone Vox 3.0 router
- USB to TTL serial adapter (CH340/FTDI)

### Tools:
- Soldering iron (if pins unpopulated)
- Jumper wires

### Software:
- Terminal emulator (PuTTY/minicom/screen)

---

## 🔌 Technical Specifications

### UART Pinout:
| Pin | Function | Connection Guide |
|-----|----------|------------------|
| GND | Ground   | Must connect |
| TX  | Transmit | Connect to RX on adapter |
| RX  | Receive  | Connect to TX on adapter |
| VCC | Power    | *Do not connect* (3.3V) |

### Terminal Settings:
Baud rate:   115200
Data bits:   8
Stop bits:   1
Parity:      None
Flow control: None

---

## 📸 Media Gallery

### UART Access Demo
Video demonstration available at:
https://github.com/user-attachments/assets/cb16c278-8b7d-44cb-b9e5-09e71b830c30

*Successful connection at 18s mark (required wire reconnection)*

### Router Images:
- Internal View 1: https://github.com/user-attachments/assets/e0d56086-0873-4aca-a1d1-1ef9fd41966b
- Internal View 2: https://github.com/user-attachments/assets/0e98267b-256c-4361-be9e-a0d92806d1fe
- Board Closeup: https://github.com/user-attachments/assets/21aac59d-8116-4d93-8dc3-fb684bb86f0b

---

## 🌐 Other Projects
Currently focusing on:
- GoFlood Project (ongoing)
- Metrics Dashboard (SDK/Requests implementation)
- Website improvements (main page + tools section)
- Computer Science study materials

Explore more:
- Dashboard: https://dashboard.birdo.uk/
- Main Site: https://birdo.uk/
- Tools: https://tools.birdo.uk/
- CS Study: https://cs.birdo.uk/
- GoFlood: https://github.com/1Birdo/GoFlood

---

## ⚠️ Legal Disclaimer
This project is strictly for:
- Educational purposes
- Ethical hacking research
- Personal device experimentation

Modifying device firmware or accessing debug interfaces may:
- Void your warranty
- Violate terms of service
- Potentially brick your device

Proceed at your own risk.
