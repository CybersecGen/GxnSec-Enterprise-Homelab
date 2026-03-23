# GxnSec Enterprise Home Lab (Archived)

## Overview
GxnSec was a self-built enterprise homelab designed to simulate a small corporate IT environment. The project focused on developing practical skills in system administration, networking, and security operations by building and testing a controlled virtual infrastructure.

This repository documents the lab design, implementation approach, challenges encountered, and key technical learnings. The environment is no longer active.

---

## Objectives
- Build a functional virtual enterprise network
- Configure and manage Active Directory
- Deploy and manage multiple operating systems
- Simulate internal attack scenarios
- Implement logging and basic detection workflows
- Develop troubleshooting skills across systems

---

## Architecture

### Core Systems
- Windows Server (Active Directory Domain Controller)
- Windows 11 Enterprise (domain-joined client)
- Ubuntu Desktop 22.04
- Kali Linux (attacker machine)
- Security server (Wazuh SIEM)
- Security Onion (network monitoring)
- Mail server (MailHog/Postfix)

### Network Design
- Isolated virtual network (no external exposure)
- Flat subnet configuration
- Internal DNS via Active Directory
- Domain-based authentication across systems

---

## Security Stack
- SIEM: Wazuh  
- Network Monitoring: Security Onion  
- Endpoint Logging: Windows Event Logs, Sysmon  
- Attack Platform: Kali Linux 

---

## Lab Implementation

### Virtualisation Setup
- Installed and configured VirtualBox
- Configured NAT Network for isolated communication
- Installed Guest Additions for usability improvements
- Used snapshots for environment recovery

### Linux Fundamentals
- File system navigation and management
- Permissions and user management
- Bash and shell scripting basics
- Process control and input/output redirection

### Enterprise Network Build
- Deployed Active Directory Domain Controller
- Joined Windows 11 client to domain
- Provisioned Ubuntu workstation/server
- Configured corporate server environment

### Supporting Services
- Configured mail server (MailHog/Postfix)
- Deployed Security Onion for network monitoring
- Built security server (Ubuntu) for SIEM
- Installed and configured Wazuh

### Detection Engineering
- Created vulnerable scenarios within the lab
- Configured basic alerts and detection rules in Wazuh

### Attack Simulation
- Provisioned Kali Linux attacker machine
- Conducted:
  - Reconnaissance and enumeration
  - Initial access (credential-based techniques)
  - Privilege escalation
  - Lateral movement
  - Data exfiltration and persistence

### Defensive Operations
- Analysed logs and alerts in SIEM
- Investigated attack activity
- Validated detection coverage

---

## Technologies and Skills
- Active Directory Domain Services
- Linux system administration (Ubuntu)
- Bash and shell scripting
- Virtualisation (VirtualBox,VMware,UTM)
- SIEM deployment and troubleshooting (Wazuh)
- Network configuration and debugging

---

## Challenges

### VM Networking and Synchronisation
- Inconsistent communication between virtual machines
- DNS misconfiguration affecting domain functionality
- Time synchronisation issues across systems

### Wazuh Stability
- Frequent crashes after short runtime
- High resource usage (CPU, memory, disk I/O)
- Elasticsearch component caused performance bottlenecks

### Hardware Constraints
**Primary system:**
- Lenovo ThinkPad (upgraded)
  - 32GB DDR4 RAM
  - 1TB SSD

**Issues encountered:**
- CPU bottlenecks under load
- Performance degradation with multiple security tools

### Platform Limitations
Migration to MacBook Pro resulted in:
- Limited x86 virtualisation support (Apple Silicon)
- Reduced performance using UTM
- Compatibility issues with enterprise tooling

### Rebuild Cycles
- Environment rebuilt multiple times due to instability
- Repeated VM reinstallation for troubleshooting

---

## Lessons Learned
- Enterprise environments are resource-intensive and require careful planning
- Active Directory depends heavily on correct DNS configuration
- SIEM platforms require dedicated resources to run reliably
- Incremental builds are more effective than full deployments
- Troubleshooting is a critical skill in both system administration and security roles

---

## Project Status
This project has been archived due to:
- Hardware limitations
- SIEM instability under constrained resources
- Time cost of repeated rebuilds

---

## Future Improvements
If rebuilt, the following changes would be made:
- Use cloud infrastructure (AWS/Azure) to remove hardware constraints
- Separate SIEM components onto dedicated systems
- Implement infrastructure-as-code (Terraform, Ansible)
- Build and test the environment in phases


---

## Summary
This lab provided practical exposure to enterprise systems, network configuration, and security tooling. Although the environment is no longer maintained, the process of building and troubleshooting it provided relevant, hands-on experience aligned with system administration and security operations roles.

---

## Author
Independent home lab project for learning and experimentation in enterprise infrastructure and cybersecurity.
