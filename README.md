<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vox 3.0 UART Shell Access</title>
    <style>
        body {
            margin: 0;
            padding: 20px;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            line-height: 1.6;
            color: #333;
            text-align: center;
        }
        
        h1, h2, h3, p, div, table, pre {
            text-align: center;
        }
        
        table {
            margin: 0 auto;
            border-collapse: collapse;
            width: auto;
            max-width: 600px;
        }
        
        th, td {
            border: 1px solid #ddd;
            padding: 8px 12px;
            text-align: center;
        }
        
        th {
            background-color: #f5f5f5;
        }
        
        pre {
            background-color: #1e1e1e;
            color: #d4d4d4;
            padding: 15px;
            border-radius: 5px;
            margin: 20px auto;
            max-width: 800px;
            overflow-x: auto;
        }
        
        .image-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin: 20px 0;
        }
        
        .image-grid img {
            width: 45%;
            max-width: 300px;
            height: auto;
        }
        
        hr {
            border: none;
            height: 1px;
            background-color: #ddd;
            margin: 30px auto;
            max-width: 800px;
        }
        
        a {
            color: #0066cc;
            text-decoration: none;
        }
        
        a:hover {
            text-decoration: underline;
        }
        
        blockquote {
            background-color: #f9f9f9;
            border-left: 4px solid #ccc;
            margin: 20px auto;
            padding: 10px 20px;
            max-width: 800px;
            text-align: left;
        }
        
        ul {
            text-align: left;
            display: inline-block;
        }
    </style>
</head>
<body>
    <div>
        <h1>🛠️ Vox 3.0 UART Shell Access</h1>
        <h3>(Universal Asynchronous Receiver-Transmitter)</h3>
        <p>Gain UART shell access on a Vodafone Vox 3.0 router.</p>
    </div>
    
    <div>
        <img src="https://github.com/user-attachments/assets/9c058053-3b5b-4f54-aab5-71c49105aeed" alt="Vox 3.0 Router" style="width: 200px; height: auto; display: inline-block;">
    </div>

    <hr>

    <h1>🏗️ Plan</h1>
    <p>I'm attempting to gain access to the device with the goal of either installing a different operating system—potentially reimaging it with OpenWRT—or modifying the existing one.</p>
    <p>Additionally, I plan to extract the original firmware to retrieve its built-in web UI dashboard. This could also help uncover potential vulnerabilities or explore basic privilege escalation opportunities within the default shell environment of the original firmware.</p>
    <p>This is purely for educational purposes. While it's unlikely that a highly proprietary device from a major corporate ISP would have vulnerabilities, it's not unheard of. Worth a shot, right? 🤷</p>

    <hr>

    <h2>📷 Preview</h2>
    <h3>UART Access Example:</h3>
    <p>At 18 seconds, the magic happens as I had to manually reconnect the wires again.</p>
    <p><a href="https://github.com/user-attachments/assets/cb16c278-8b7d-44cb-b9e5-09e71b830c30">Video Link</a></p>
    
    <h3>Router Closeups:</h3>
    <div class="image-grid">
        <img src="https://github.com/user-attachments/assets/e0d56086-0873-4aca-a1d1-1ef9fd41966b" alt="Router closeup 1"/>
        <img src="https://github.com/user-attachments/assets/0e98267b-256c-4361-be9e-a0d92806d1fe" alt="Router closeup 2"/>
        <img src="https://github.com/user-attachments/assets/21aac59d-8116-4d93-8dc3-fb684bb86f0b" alt="Router closeup 3"/>
        <img src="https://github.com/user-attachments/assets/bb7b793b-454f-48b8-92c0-b2904dcdeab2" alt="Router closeup 4"/>
    </div>

    <hr>

    <h2>📖 Description</h2>
    <p>This repository documents how to access a UART serial console on the Vodafone Vox 3.0 router, which can provide direct shell access to the underlying Linux system. This can be useful for research, debugging, or developing custom firmware.</p>
    <blockquote>
        <strong>Note:</strong> This is intended for educational and personal research purposes only. Do not attempt this on devices you do not own or have explicit permission to access.
    </blockquote>

    <hr>

    <h2>🔧 What You Need</h2>
    <table>
        <tr>
            <th>Item</th>
        </tr>
        <tr>
            <td>A Vodafone Vox 3.0 router</td>
        </tr>
        <tr>
            <td>USB to TTL serial adapter (e.g., CH340, FTDI)</td>
        </tr>
        <tr>
            <td>Soldering tools (if UART pins are not populated)</td>
        </tr>
        <tr>
            <td>Terminal emulator (PuTTY, minicom, screen, etc.)</td>
        </tr>
    </table>

    <hr>

    <h2>📡 UART Pinout (Typical)</h2>
    <table>
        <tr>
            <th>Pin</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>GND</td>
            <td>Ground</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Transmit</td>
        </tr>
        <tr>
            <td>RX</td>
            <td>Receive</td>
        </tr>
        <tr>
            <td>VCC</td>
            <td><em>Do not connect</em> (usually 3.3V)</td>
        </tr>
    </table>

    <hr>

    <h2>🖥️ Connection Settings</h2>
    <table>
        <tr>
            <th>Setting</th>
            <th>Value</th>
        </tr>
        <tr>
            <td><strong>Baud rate</strong></td>
            <td>115200</td>
        </tr>
        <tr>
            <td><strong>Data bits</strong></td>
            <td>8</td>
        </tr>
        <tr>
            <td><strong>Stop bits</strong></td>
            <td>1</td>
        </tr>
        <tr>
            <td><strong>Parity</strong></td>
            <td>None</td>
        </tr>
        <tr>
            <td><strong>Flow control</strong></td>
            <td>None</td>
        </tr>
    </table>

    <hr>

    <h2>⚠️ Disclaimer</h2>
    <pre>(*I am currently still working on the GoFlood Project but exploring different areas,
Other projects like my Metrics Dashboard via SDKs/Requests is still under-development.
I'm also making improvements / tweaks to my main page and fixing errors + implementing my tools + CS study page fully)</pre>
    
    <p><em>Check out the pages here</em>:</p>
    <ul>
        <li><a href="https://dashboard.birdo.uk/">Dashboard</a></li>
        <li><a href="https://birdo.uk/">Main</a></li>
        <li><a href="https://tools.birdo.uk/">Tools</a></li>
        <li><a href="https://cs.birdo.uk/">Study</a></li>
        <li><a href="https://github.com/1Birdo/GoFlood">GoFlood</a></li>
    </ul>
    
    <p>This project is for educational and ethical hacking research only. Modifying your device firmware or accessing debug interfaces may void your warranty or violate terms of service. Proceed at your own risk.</p>
</body>
</html>
