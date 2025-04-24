# Cybersecurity SIEM Projects

This repository contains three cybersecurity lab projects completed for CSE 804, focusing on security monitoring and attack simulation. The projects demonstrate the setup and use of SIEM, HIDS, and NIDS, along with simulations of DLL Hijacking and Shellshock attacks, with detection using Wazuh.

## Projects
1. **SIEM, HIDS, and NIDS Setup**
   - Tools: Elasticsearch, Kibana, Filebeat, Wazuh, Suricata
   - Objective: Deploy a SIEM solution with HIDS and NIDS for log analysis and intrusion detection.
   - [Details](./SIEM-HIDS-NIDS-Setup/README.md)

2. **DLL Hijacking Simulation**
   - Tools: Sysmon, SysmonSimulator, Wazuh
   - Objective: Simulate DLL injection on Windows 10 and detect it using Sysmon and Wazuh.
   - [Details](./DLL-Hijacking/README.md)

3. **Shellshock Attack Simulation**
   - Tools: Apache2, Wazuh, curl
   - Objective: Simulate a Shellshock attack on an Apache2 server and detect it using Wazuh rules.
   - [Details](./Shellshock-Attack/README.md)

## Setup
- **Prerequisites**: VirtualBox, Ubuntu, Kali Linux, Windows 10, Visual Studio 2022.
- **Network**: VMs configured on the 192.168.1.0/24 subnet (SIEM and Shellshock) or 10.42.0.238 (DLL Hijacking).
- Follow individual project READMEs for detailed setup instructions.

## Usage
- Clone the repository: `git clone https://github.com/yourusername/Cybersecurity-Lab-Projects.git`
- Navigate to each project folder and follow the respective README for execution.

## License
MIT License
