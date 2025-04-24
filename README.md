# Cybersecurity SIEM Projects

This repository contains three cybersecurity lab projects completed for CSE 804, focusing on security monitoring and attack simulation. The projects demonstrate the setup and use of SIEM, HIDS, and NIDS, along with simulations of DLL Hijacking and Shellshock attacks, with detection using Wazuh.

**Don't want to waste time reading the README?** Visit this link for a quick overview:  
[Project Documentation](https://docs.google.com/document/d/10zDjF0QwqrHBUMmVupDMyX7rqgN1ife3hQSYFeAAPu8/edit?tab=t.0)

## Projects
# SIEM, HIDS, and NIDS Setup

This project demonstrates the setup of a SIEM solution using Elasticsearch (7.17.13), Kibana, and Filebeat, integrated with Wazuh Manager (4.7.4) for HIDS and Suricata for NIDS.

## Environment
- **Ubuntu VM**: IP 192.168.1.11 (hosts SIEM, HIDS, NIDS)
- **Kali VM**: IP 192.168.1.12 (attacker)
- **Network**: 192.168.1.0/24 subnet, bridged adapter in VirtualBox

## Installation
1. Install dependencies:
   ```bash
   sudo apt install git curl
cd /opt
git clone https://github.com/samiul008ghub/sour_setup/
cd soc_setup
chmod +x setup_script.sh
./setup_script.sh

Verification
Elasticsearch: Access via browser at 192.168.1.11:port.
Kibana: View logs on the Kibana dashboard.
Filebeat: Confirm logs in Kibana.
Suricata: Check alerts in Kibana.
Wazuh: Verify dashboard (no agents connected, all components at zero).


# DLL Hijacking Simulation
This project simulates a DLL injection attack on a Windows 10 machine (IP: 10.42.0.238) and detects it using Sysmon and Wazuh.

## Environment
- **Windows 10**: IP 10.42.0.238
- **Tools**: Sysmon, SysmonSimulator, Visual Studio Community 2022, Wazuh

## Prerequisites
- Install Visual Studio Community 2022: [Download](https://visualstudio.microsoft.com/vs/community/).
- Install Sysmon (run as administrator).

## Setup
1. Install Sysmon:
   - Download Sysmon and install the driver (command not specified in the workbook).
2. Compile SysmonSimulator:
   - Open `sysmonsimulator.c` in Visual Studio.
   - Build the project to generate `SysmonSimulator.exe` in the `debug` folder.
3. Run the simulation:
   ```cmd
   SysmonSimulator.exe -h
   SysmonSimulator.exe -eid 8

Detection
Sysmon logs system activity to the Windows Event Log.
Wazuh collects and analyzes logs, generating alerts for detected DLL injection attempts.

# Shellshock Attack Simulation
This project simulates a Shellshock attack on an Apache2 server (Ubuntu) and detects it using Wazuh with custom rules.

## Environment
- **Ubuntu VM**: IP 192.168.1.11 (Apache2 server)
- **Kali VM**: IP 192.168.1.12 (attacker)
- **Network**: 192.168.1.0/24 subnet

## Setup
1. Install Apache2 on Ubuntu:
   ```bash
   sudo apt update
   sudo apt install apache2
   sudo ufw allow 'Apache'
   sudo systemctl status apache2

Detection
Wazuh captures HTTP traffic using an HTTP decoder.
Rule ID 31168 triggers alerts for Shellshock payloads in the User-Agent header.
Three attack attempts were logged (filter by rule.description:"Shellshock attack detected" and Agent 002).

Files
web_rules.xml: Wazuh rule configuration for Shellshock detection.
ossec.conf: Modified Wazuh agent configuration (snippet).
screenshots/: Wazuh dashboard showing three alerts.

Notes
Rule ID 31168 corresponds to CVE-2014-6271 (Shellshock).
Customize Wazuh dashboard columns for better log visibility.

