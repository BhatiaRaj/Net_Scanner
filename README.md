# Network Scanner Tool for Cyber Security Red Teaming

A Python-based network scanner designed for identifying active devices, open ports, running services, and potential vulnerabilities within a specified IP range. This tool is intended for educational purposes and authorized security testing (Red Teaming).

---

**[!] DISCLAIMER [!]**

**This tool is intended for authorized security testing and educational purposes ONLY.**
**Using this tool against networks or systems without explicit prior mutual consent is illegal and unethical.**
**The user is solely responsible for abiding by all applicable local, state, national, and international laws.**
**The developers assume no liability and are not responsible for any misuse or damage caused by this program.**
**ALWAYS ensure you have EXPLICIT PERMISSION before scanning any target.**

---

## Features

*   **User-Defined Scans:**
    *   Specify IP ranges (e.g., `192.168.1.1-192.168.1.255`, `192.168.1.0/24`, single IP).
    *   Choose scan types:
        *   TCP Connect Scan (`tcp_connect`)
        *   TCP SYN Scan (`syn`) - *Requires root/administrator privileges*
        *   UDP Scan (`udp`) - *Requires root/administrator privileges for best results*
*   **Device Discovery:**
    *   Identifies active hosts using ICMP pings.
    *   Retrieves MAC addresses (for local networks via ARP) and attempts MAC vendor lookup.
    *   Basic OS guessing based on TTL values.
*   **Port Scanning:**
    *   Scans for open TCP and UDP ports.
    *   Option to scan common ports, a custom list/range, or all 65535 ports.
*   **Service Detection & Version Fingerprinting:**
    *   Grabs banners from open TCP ports.
    *   Basic parsing of banners to identify service names and versions.
    *   Guesses common UDP services based on port numbers.
*   **Vulnerability Assessment (Illustrative):**
    *   Integrates a *mock/sample* CVE database.
    *   Flags potential vulnerabilities based on detected service versions.
    *   **Note:** This is for demonstration; real-world assessment requires comprehensive, up-to-date databases.
*   **Comprehensive Reporting:**
    *   Generates a detailed text-based report (`scan_report.txt` by default) summarizing:
        *   Discovered devices (IP, MAC, OS guess, Vendor).
        *   Open ports, detected services, and versions.
        *   Identified potential vulnerabilities with descriptions, severity, and remediation advice (from the mock database).
*   **Command-Line Interface:**
    *   User-friendly CLI with clear options.
*   **Threading:**
    *   Uses threading for concurrent scanning of multiple hosts to improve speed.

## Requirements

*   Python 3.x
*   Libraries:
    *   `scapy`
    *   `mac-vendor-lookup`

## Installation

1.  **Clone the repository (or download the script):**
    ```bash
    git clone https://github.com/BhatiaRaj/Net_Scanner.git
    cd <repository_directory>
    ```

2.  **Install Python dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    (If no `requirements.txt` is provided, install manually):
    ```bash
    pip install scapy mac-vendor-lookup
    ```
    *Note: `mac-vendor-lookup` may download/update its OUI database on the first run, requiring an internet connection.*

## Usage

The script requires command-line arguments to specify the target and scan options.

**Basic Syntax:**

```bash
sudo python3 net_scanner.py <IP_RANGE> [OPTIONS]
