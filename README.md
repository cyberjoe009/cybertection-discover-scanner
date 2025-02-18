# cybertection-discover-scanner
Similar to netdiscover but more advanced

To Use: 
MUST RUN IN A VERTUAL ENVIRONMENT

python3 -m venv .venv        # Create
source .venv/bin/activate   # Activate (Linux/macOS)
.venv\Scripts\activate      # Activate (Windows)

Install Libraries: pip install scapy requests python-nmap

macaddress.io API Key: Get an API key from macaddress.io and replace <YOUR_API_KEY> with your actual key.

Run with Root Privileges: sudo ./net_discover.py -i <your_interface> -r <ip_range>

Remember to be very careful with ARP poisoning if you decide to implement it.  GUI development is a separate project and would require a different approach.  Let me know if you have any other questions.

Install Scapy: pip install scapy

Save: Save the code as a Python file (e.g., net_discover.py).

oui.txt: Create a file named oui.txt in the same directory as your script. This file should contain OUI (Organizationally Unique Identifier) to vendor mappings. You can find up-to-date OUI lists online (search for "OUI database" or "IEEE OUI"). A simple format would be:

000000 Cisco
000001 Hewlett-Packard
...

Permissions: Make the script executable: chmod +x net_discover.py

Run with Root Privileges: sudo ./net_discover.py -i <your_interface> -r <ip_range> (e.g., sudo ./net_discover.py -i eth0 -r 192.168.1.0/24) or simply sudo ./net_discover.py -i <your_interface> to scan the network of that interface.

___________________________________________________________________________________________________________

 Explanations:

Asynchronous Scanning: The scan function is now asynchronous using async and await. asyncio.to_thread is used to make the Scapy srp function compatible with asyncio.
Service Discovery (Nmap): The discover_services function uses the python-nmap library to scan for open ports and services using Nmap. It also performs basic OS detection. You'll need to install python-nmap: pip install python-nmap.
Parallel Nmap Scans: The scan_network function now uses a ThreadPoolExecutor to run the Nmap scans in parallel, significantly improving performance.
Online Vendor Lookup: The get_mac_vendor function now uses the macaddress.io API for online MAC address lookups. You will need to create an account and obtain an API key from macaddress.io and insert it into the code.
OS Fingerprinting: Basic OS fingerprinting is now done as part of the Nmap service scan. More advanced OS fingerprinting would require deeper packet analysis.
ARP Poisoning: I have not included ARP poisoning code in this example. ARP poisoning is a very powerful technique but also potentially very dangerous. It should only be used on networks you own and with extreme caution. If you want to implement it, please research it thoroughly first and be fully aware of the ethical and legal implications.
GUI: Creating a GUI for this tool would require a separate GUI library (e.g., Tkinter, PyQt, Kivy). This is a significant undertaking and is beyond the scope of this example.
Error Handling: Improved error handling.
____________________________________________________________________________________________________________
Virtual Environments (Recommended): If you're working on multiple Python projects, it's highly recommended to use virtual environments. This isolates the dependencies for each project and prevents conflicts.
Bash

python3 -m venv .venv  # Create a virtual environment
source .venv/bin/activate  # Activate the environment (Linux/macOS)
.venv\Scripts\activate  # Activate the environment (Windows)
pip install scapy requests python-nmap  # Install inside the virtual environment
Permissions: Make sure you have the necessary permissions to install packages. If you're on Linux/macOS, you might need to use sudo pip install python-nmap (but virtual environments are preferred).
Pip Version: Ensure your pip version is up-to-date: pip install --upgrade pip
Python Version: Make sure you're using the correct pip for the Python version you're running your script with (e.g., pip3 for Python 3).
After installing python-nmap correctly, the Nmap-related parts of your Python script should work
