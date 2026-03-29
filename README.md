# Enterprise Security Lab (Implementation & Lessons Learned)

## Overview
GxnSec is a self-built enterprise homelab simulating a small corporate IT environment. It focused on developing skills in system administration, networking, and security operations through a controlled virtual infrastructure.
This repository covers the lab’s design, implementation, challenges, and key technical learnings. The environment is no longer active.

---

## Objectives
- Build a functional virtual enterprise network
- Configure and manage Active Directory
- Deploy and manage multiple operating systems
- Simulate internal attack scenarios
- Implement logging and basic detection workflows
- Develop troubleshooting skills across systems**

---

## Architecture

### Core Infrastructure
Domain Controller: Windows Server (AD DS, DNS, DHCP, SSO)
Endpoints: Windows 11 Enterprise, Ubuntu Desktop
Security Stack: Wazuh (SIEM), Security Onion (network monitoring)
Attack Platform: Kali Linux
Supporting Services: Mail server (Postfix / MailHog)

---

## Network Configuration

### Virtual Network
| Setting | Value |
|--------|------|
| Network Type | VirtualBox NAT Network |
| Network Name | `gxnsec-nat` |
| Subnet | `10.0.0.0/24` |
| Usable Range | `10.0.0.1 – 10.0.0.254` |
| DHCP Scope | `10.0.0.100 – 10.0.0.200` |

---

### Host & Role Allocation

| Hostname | IP Address | Role |
|----------|-----------|------|
| `gxnsec-dc` | `10.0.0.5` | Domain Controller (DNS, DHCP, SSO) |
| `gxnsec-admin` | `10.0.0.8` | Corporate Server |
| `gxnsec-sec-box` | `10.0.0.10` | SIEM / Security Server |
| `gxnsec-sec-work` | `10.0.0.103` *(DHCP optional)* | Security Monitoring Workstation |
| `gxnsec-win-client` | `10.0.0.100` *(DHCP)* | Windows Endpoint |
| `gxnsec-linux-client` | `10.0.0.101` *(DHCP)* | Linux Endpoint |
| `gxnsec-attacker` | Dynamic | Attacker Machine |

---

## Virtual Machine Specifications

| VM Name | OS | CPU / RAM | Storage |
|--------|----|-----------|--------|
| `gxnsec-dc` | Windows Server 2025 | 2 vCPU / 4GB | 50GB |
| `gxnsec-win-client` | Windows 11 Enterprise | 2 vCPU / 4GB | 80GB |
| `gxnsec-linux-client` | Ubuntu 22.04 Desktop | 1 vCPU / 2GB | 80GB |
| `gxnsec-sec-work` | Security Onion | 1 vCPU / 2GB | 55GB |
| `gxnsec-sec-box` | Ubuntu 22.04 | 2 vCPU / 4GB | 80GB |
| `gxnsec-corp-svr` | Ubuntu Server 22.04 | 1 vCPU / 2GB | 25GB |
| `gxnsec-attacker` | Kali Linux 2024.2 | 1 vCPU / 2GB | 55GB |

---

## Identity & Access (Lab Credentials)

| Account | Host | Purpose |
|--------|------|--------|
| `Administrator` | Domain Controller | Domain admin |
| `johnd@corp.gxnsec-dc.com` | Windows Client | Standard user |
| `janed@linux-client` | Linux Client | Standard user |
| `gxnsec-sec-work` | Security Workstation | Analyst access |
| `sec-work@sec-box` | Security Server | SIEM access |
| `gxnsec-admin@corp-svr` | Corporate Server | Admin account |
| `attacker@attacker` | Attacker VM | Offensive testing |

---

## Security Stack

| Component | Tool | Purpose |
|----------|------|--------|
| SIEM | Wazuh | Log collection, correlation, alerting |
| Network Monitoring | Security Onion | Traffic analysis, IDS |
| Endpoint Logging | Sysmon + Windows Event Logs | Endpoint visibility |
| Attack Platform | Kali Linux | Adversary simulation |


---

## Implementation

### 1. Virtualisation & Network Setup
- Built using VirtualBox NAT Network (isolated environment)
- Configured internal communication across all hosts
- Used snapshots for rollback and recovery

### 2. Active Directory Deployment
- Installed and configured Domain Controller
- Configured DNS for domain resolution
- Joined Windows client to domain
- Centralised authentication across systems

### 3. System Provisioning
- Deployed Windows and Linux endpoints
- Configured user accounts and permissions
- Built supporting infrastructure (mail server, internal services)

### 4. SIEM & Monitoring Deployment
- Installed Wazuh on dedicated security server
- Integrated endpoint logging (Sysmon, Windows logs)
- Deployed Security Onion for network-level monitoring
- Created basic alerting and detection rules

---

## Attack Simulation (Red Team Activity)

Simulated realistic attack scenarios using Kali Linux:

- Reconnaissance & enumeration  
- Credential-based initial access  
- Privilege escalation  
- Lateral movement across domain  
- Persistence techniques  
- Data exfiltration  

---

## Defensive Operations (SOC Workflow)

- Monitored alerts in Wazuh SIEM  
- Investigated suspicious activity  
- Correlated logs across endpoints and network  
- Validated detection coverage  
- Identified gaps in visibility and logging  

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
