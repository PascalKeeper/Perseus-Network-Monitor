Perseus Network Monitor

Copyright Joseph Peransi, 2026.

Perseus Network Monitor is a production-ready, Windows system-level backend designed for real-time network traffic analysis, privacy hardening, and dynamic firewall management. Built with Python and Flask, it serves as the core engine for correlating process activity with network I/O, detecting suspicious outbound connections, and managing system-level tools.

Prerequisites

Operating System: Windows 10/11 (Requires Windows Firewall and netsh).

Python: Python 3.8 or higher.

Privileges: Administrator rights are strictly required for process resolving, I/O monitoring, and firewall rule modification.

Installation

Install Python Dependencies:
Open an elevated command prompt (Run as Administrator) and install the required packages:

pip install flask flask-cors psutil


Directory Structure Setup:
The engine expects a specific directory structure for its external scripts. Create the following directory:

mkdir C:\Perseus\scripts


Deploy External Tools:
Place the corresponding operational scripts into C:\Perseus\scripts\:

Privacy Hardening Script.py

ROG_BE92_Signal_Optimizer.py

secure_gaming_firewall.ps1

network optimizer with reset.bat

Deploy the UI:
Ensure perseus_dashboard.html is located in the exact same directory as the main Perseus Engine Python script.

Usage

Launch the Engine:
Right-click your command prompt or terminal and select Run as Administrator. Execute the main engine script:

python "Perseus Engine Privacy Hardening Script.py"


Access the Dashboard:
Once initialized, the system monitor will be online. Open your web browser and navigate to:

http://localhost:5500


API Endpoints

The backend exposes a RESTful API for frontend integration:

GET / - Serves the web UI dashboard.

GET /api/monitor - Returns real-time JSON array of active connections, PIDs, processes, remote IPs, ports, and calculated bandwidth (Bps). Includes malicious heuristic flagging.

POST /api/firewall/block - Adds an outbound and inbound Windows Firewall block rule for a provided JSON payload: {"ip": "x.x.x.x"}.

POST /api/firewall/whitelist - Adds an outbound Windows Firewall allow rule for a provided JSON payload: {"ip": "x.x.x.x"}.

POST /api/tools/run - Executes integrated system tools. Payload: {"script": "<alias>"}. Valid aliases: hardening, optimizer, firewall_rules, net_reset.

Security Notice

This application actively modifies system-level firewall rules and executes shell scripts. Do not expose port 5500 to external networks. Ensure C:\Perseus\scripts is secured and restricted to Administrator write-access only to prevent privilege escalation or arbitrary code execution.

License

This project is licensed under the GNU General Public License v3.0. See the LICENSE file for details.
