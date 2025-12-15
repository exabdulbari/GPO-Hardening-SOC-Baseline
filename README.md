# GPO-Hardening-SOC-Baseline

## Project Overview

This project demonstrates the implementation of an enterprise-grade Windows Group Policy Object (GPO) hardening baseline focused on preventing attacker evasion and ensuring security visibility.

The lab simulates a real-world enterprise environment where attackers attempt to disable security controls, stop logging services, and hide malicious activity.

The goal of this project is to enforce firewall protection, protect critical security services, and enable SOC-grade auditing for effective detection and investigation.

## Threat Model

This project focuses on common attacker techniques used after initial access, including:

- Disabling or weakening host-based security controls (firewall and antivirus)
- Stopping or tampering with logging services to reduce detection visibility
- Executing malicious processes while attempting to evade audit and monitoring controls

The hardening policies implemented in this project are designed to prevent these techniques and ensure that security-relevant activity remains visible for detection and investigation.
This reflects real-world attacker behavior observed in enterprise Windows environments.

## Hardening Controls Implemented

### Firewall Hardening
- Enforced Windows Defender Firewall enabled for Domain and Standard profiles
- Blocked inbound connections by default
- Prevented users and applications from disabling the firewall or adding exceptions

### Microsoft Defender Protection
- Enforced Microsoft Defender Antivirus Service startup as Automatic
- Configured service recovery to automatically restart on failure
- Removed INTERACTIVE permissions from the Defender service
- Restricted service stop permissions to prevent attacker tampering

### Windows Event Log Protection
- Enforced Windows Event Log service startup as Automatic
- Prevented non-system accounts from stopping the Event Log service
- Removed INTERACTIVE permissions to protect logging availability

### Audit Policy Configuration
- Enabled SOC-critical Logon and Logoff auditing (success and failure)
- Enabled Process Creation auditing with command-line logging
- Enabled audit policies to detect policy and authentication changes

### Security Log Protection
- Increased Security log maximum size to retain sufficient evidence
- Configured log retention to prevent event overwriting
- Restricted guest access to the Security log

## Screenshots

The following screenshots provide evidence of the implemented hardening controls:

- **Firewall enforcement via Group Policy**
  - `gpo-firewall-all-profiles-enforced.png`  
    Windows Defender Firewall enforced for Domain, Private, and Public profiles using Group Policy
    
- **Microsoft Defender service protection**
  - `defender-service-startup-policy.png`
  - `defender-service-permissions-hardened.png`  
    Defender service enforced to start automatically and protected from attacker tampering
    
- **Windows Event Log service protected from tampering**
  - `eventlog-service-startup-policy.png`
  - `eventlog-service-permissions-hardened.png`  
    Event logging service enforced and protected to maintain SOC visibility
    
- **SOC-critical audit configuration**
  - `audit-process-creation-enabled.png`
  - `command-line-logging-enabled.png`  
    Process creation auditing enabled with command-line visibility

- **Security log retention and protection**
  - `security-log-retention-policy.png`  
    Security log size increased and overwrite protection enforced

    
