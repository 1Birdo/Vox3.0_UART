# 🛠️ Vox 3.0 UART Shell Access
### (Universal Asynchronous Receiver-Transmitter)

Gain UART shell access on a Vodafone Vox 3.0 router.
----

## 📷 Preview
### UART Access Example:

At 18 Seconds is where the magic begins as i had to manual reconnect the wires again

https://github.com/user-attachments/assets/cb16c278-8b7d-44cb-b9e5-09e71b830c30

### Router Closeups:
![Image 1](https://github.com/user-attachments/assets/21aac59d-8116-4d93-8dc3-fb684bb86f0b)
![Image 2](https://github.com/user-attachments/assets/bb7b793b-454f-48b8-92c0-b2904dcdeab2)

---

## 📖 Description

This repository documents how to access a UART serial console on the Vodafone Vox 3.0 router, which can provide direct shell access to the underlying Linux system. This can be useful for research, debugging, or developing custom firmware.

> **Note:** This is intended for educational and personal research purposes only. Do not attempt this on devices you do not own or have explicit permission to access.

---

## 🔧 What You Need

- A Vodafone Vox 3.0 router
- USB to TTL serial adapter (e.g., CH340, FTDI)
- Soldering tools (if UART pins are not populated)
- Terminal emulator (PuTTY, minicom, screen, etc.)

---

## 📡 UART Pinout (Typical)

| Pin | Description |
|-----|-------------|
| GND | Ground      |
| TX  | Transmit    |
| RX  | Receive     |
| VCC | *Do not connect* (usually 3.3V) |

---

## 🖥️ Connection Settings

- **Baud rate:** 115200
- **Data bits:** 8  
- **Stop bits:** 1  
- **Parity:** None  
- **Flow control:** None

---

## ⚠️ Disclaimer

This project is for educational and ethical hacking research only. Modifying your device firmware or accessing debug interfaces may void your warranty or violate terms of service. Proceed at your own risk.
