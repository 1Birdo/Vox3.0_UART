<div style="text-align: center;">
  <h1>🛠️ Vox 3.0 UART Shell Access</h1>
  <h3>(Universal Asynchronous Receiver-Transmitter)</h3>
  <p>Gain UART shell access on a Vodafone Vox 3.0 router.</p>
</div>

  <div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/9c058053-3b5b-4f54-aab5-71c49105aeed" alt="Vox 3.0 Router" style="width: 200px; height: auto; display: inline-block;">
  </div>

---


# 🏗️ Plan

I'm attempting to gain access to the device with the goal of either installing a different operating system—potentially reimaging it with OpenWRT—or modifying the existing one.

Additionally, I plan to extract the original firmware to retrieve its built-in web UI dashboard. This could also help uncover potential vulnerabilities or explore basic privilege escalation opportunities within the default shell environment of the original firmware.

This is purely for educational purposes. While it's unlikely that a highly proprietary device from a major corporate ISP would have vulnerabilities, it's not unheard of. Worth a shot, right? 🤷

---

## 📷 Preview
### UART Access Example:

At 18 seconds, the magic happens as I had to manually reconnect the wires again.

[Video Link](https://github.com/user-attachments/assets/cb16c278-8b7d-44cb-b9e5-09e71b830c30)

### Router Closeups:

<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: space-around;">
  <img src="https://github.com/user-attachments/assets/e0d56086-0873-4aca-a1d1-1ef9fd41966b" style="width: 45%; max-width: 300px;"/>
  <img src="https://github.com/user-attachments/assets/0e98267b-256c-4361-be9e-a0d92806d1fe" style="width: 45%; max-width: 300px;"/>
  <img src="https://github.com/user-attachments/assets/21aac59d-8116-4d93-8dc3-fb684bb86f0b" style="width: 45%; max-width: 300px;"/>
  <img src="https://github.com/user-attachments/assets/bb7b793b-454f-48b8-92c0-b2904dcdeab2" style="width: 45%; max-width: 300px;"/>
</div>

---

## 📖 Description

This repository documents how to access a UART serial console on the Vodafone Vox 3.0 router, which can provide direct shell access to the underlying Linux system. This can be useful for research, debugging, or developing custom firmware.

> **Note:** This is intended for educational and personal research purposes only. Do not attempt this on devices you do not own or have explicit permission to access.

---

## 🔧 What You Need

| Item                                  |
|---------------------------------------|
| A Vodafone Vox 3.0 router             |
| USB to TTL serial adapter (e.g., CH340, FTDI) |
| Soldering tools (if UART pins are not populated) |
| Terminal emulator (PuTTY, minicom, screen, etc.) |

---

## 📡 UART Pinout (Typical)

| Pin | Description         |
|-----|---------------------|
| GND | Ground             |
| TX  | Transmit           |
| RX  | Receive            |
| VCC | *Do not connect* (usually 3.3V) |


---

## 🖥️ Connection Settings

| Setting       | Value    |
|---------------|----------|
| **Baud rate** | 115200   |
| **Data bits** | 8        |
| **Stop bits** | 1        |
| **Parity**    | None     |
| **Flow control** | None  |

---

## ⚠️ Disclaimer

```bash
(*I am currently still working on the GoFlood Project but exploring different areas,
Other projects like my Metrics Dashboard via SDKs/Requests is still under-development.
I'm also making improvements / tweaks to my main page and fixing errors + implementing my tools + CS study page fully)
```

*Check out the pages here*:
- [Dashboard](https://dashboard.birdo.uk/)
- [Main](https://birdo.uk/)
- [Tools](https://tools.birdo.uk/)
- [Study](https://cs.birdo.uk/)
- [GoFlood](https://github.com/1Birdo/GoFlood)


This project is for educational and ethical hacking research only. Modifying your device firmware or accessing debug interfaces may void your warranty or violate terms of service. Proceed at your own risk.
