# GxnSec Enterprise Home Lab (Archived)

## Overview
GxnSec was a self-built enterprise home lab designed to simulate a small corporate environment. The purpose of the project was to gain hands-on experience with system administration, networking, and security operations by building and testing a controlled virtual infrastructure.

This repository documents the architecture, configuration approach, issues encountered, and key lessons learned. The lab is no longer active.

---

## Objectives
- Build a functional virtual enterprise network
- Configure and manage Active Directory
- Deploy and manage multiple operating systems
- Simulate attack scenarios from an internal adversary
- Implement basic logging and detection workflows
- Develop practical troubleshooting skills across systems

---

## Architecture

### Core Systems
- Windows Server (Active Directory Domain Controller)
- Windows 11 Enterprise (domain-joined client)
- Ubuntu Desktop 22.04
- Kali Linux (attacker machine)
- Security server (Wazuh SIEM)
- Security Onion (network monitoring)
- Postfix email server

### Network Design
- Isolated virtual network (no external exposure)
- Flat subnet configuration
- Domain-based authentication and internal DNS resolution

---

## Security Stack
- SIEM: Wazuh
- Network monitoring: Security Onion
- Endpoint logging: Windows Event Logs, Sysmon
- Attack platform: Kali Linux

---

## Attack Simulation
The lab was used to simulate a basic attack chain within a controlled environment:

1. Reconnaissance (network scanning and enumeration)  
2. Initial access (credential-based techniques)  
3. Privilege escalation  
4. Lateral movement across domain-joined systems  
5. Detection attempts using SIEM tooling  

---

## Technologies and Skills
- Active Directory Domain Services
- Linux administration (Ubuntu)
- Bash and shell scripting
- Virtualisation platforms (VirtualBox, UTM)
- SIEM deployment and troubleshooting (Wazuh)
- Network configuration and debugging

---

## Challenges

### VM Networking and Synchronisation
- Inconsistent communication between virtual machines on an isolated network
- DNS misconfiguration impacting domain functionality
- Dependency on correct time synchronisation across systems

### Wazuh Stability
- Wazuh would run briefly and then crash
- Likely due to resource constraints (CPU, memory, disk I/O)
- Elasticsearch component particularly resource-intensive

### Hardware Constraints
**Primary system:**
- Lenovo ThinkPad (upgraded)
  - 16GB DDR4 RAM
  - 1TB SSD

**Observed issues:**
- CPU bottlenecks under load
- Performance degradation when running multiple security tools

### Platform Limitations
Migration to a MacBook Pro introduced additional issues:
- Limited support for x86 virtualisation on Apple Silicon
- Reduced performance using UTM
- Compatibility issues with some enterprise tooling

### Rebuild Cycles
- Environment was rebuilt multiple times due to instability and configuration errors
- Frequent reinstallation of virtual machines to troubleshoot issues

---

## Lessons Learned
- Enterprise-style environments are resource-intensive and require planning around hardware limits
- Active Directory is highly dependent on correct DNS and network configuration
- SIEM platforms require dedicated resources to run reliably
- Building environments incrementally is more effective than deploying all components at once
- Troubleshooting across systems is a critical skill in both administration and security roles

---

## Project Status
This project has been archived due to:
- Hardware limitations
- Stability issues with security tooling
- Time cost of repeated rebuilds

---

## Future Improvements
If rebuilt, the following changes would be made:
- Use cloud infrastructure (e.g. AWS or Azure) to remove hardware constraints
- Separate SIEM components onto dedicated resources
- Use infrastructure-as-code (Terraform, Ansible) for repeatable builds
- Adopt a phased deployment approach

---

## Summary
This lab provided practical exposure to enterprise systems, network configuration, and security tooling. Although the environment is no longer maintained, the process of building and troubleshooting it provided relevant, hands-on experience aligned with entry-level system administration and security operations roles.

---

## Author
Independent home lab project for learning and experimentation in enterprise infrastructure and cybersecurity.
