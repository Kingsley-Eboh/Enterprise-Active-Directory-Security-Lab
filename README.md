Enterprise Active Directory Security Lab

Blue Team Detection Engineering | Windows Server 2022 | VirtualBox

## Project Summary

This project is a production-modeled Active Directory (AD) security lab designed to simulate enterprise authentication, access control, attack activity, and Blue Team detection workflows.

It demonstrates hands-on experience with:

Active Directory administration

Role-Based Access Control (RBAC)

Advanced Group Policy engineering

Windows security event analysis

Authentication monitoring

PowerShell telemetry configuration

Account lockout & brute-force detection

Detection validation through controlled attack simulation

## Objective

The goal of this lab is to understand and validate how authentication events, privilege changes, process execution, and PowerShell activity are logged, monitored, and analyzed in an enterprise Windows domain environment.

It bridges the gap between system administration and defensive security monitoring, providing a realistic environment for Blue Team skill development.

🏗 Lab Architecture
Component	Description
Domain Controller	Windows Server 2022
Domain Name	king.local
Client Machine	Domain-joined Windows client (King-Client)
Network	Isolated VirtualBox internal lab network
🔐 Active Directory Architecture

Organizational Unit (OU) Design

King-Users

King-Admins

King-Computers

Structured OU design reflects enterprise separation of duties and scalable policy enforcement.

👥 Role-Based Access Control (RBAC)

Security Groups Created

Blue-Team (Defensive Operations)

Red-Team (Offensive Simulation)

Purple-Team (Hybrid Operations)

Users assigned to groups simulate realistic enterprise access delegation and privilege separation, demonstrating understanding of:

Least privilege principle

Group-based access management

Administrative tiering concepts

🛠 Group Policy & Security Engineering
Password & Account Lockout Enforcement

Configured domain-level security controls:

Minimum password length: 10

Password complexity enabled

Password history enforced

Account lockout threshold: 5 failed attempts

Lockout duration: 15 minutes

Detection Validated:

Event ID 4740 – Account Locked Out

Event ID 4625 – Failed Logon

Successfully simulated brute-force attacks and validated centralized logging.

📊 Advanced Audit Policy Engineering

Created a dedicated security-focused GPO without modifying the default domain policy. Enabled detailed auditing:

Authentication Monitoring

4624 – Successful Logon

4625 – Failed Logon

4672 – Special Privileges Assigned

4768 – Kerberos TGT Request

4769 – Service Ticket Request

Account & Privilege Monitoring

4720 – User Account Created

4728 – User Added to Security Group

Directory Service Changes

Process Monitoring

4688 – Process Creation (with full command-line logging enabled)

4719 – Audit policy modifications

Enabled audit subcategory override enforcement to capture granular activity beyond default Windows logging.

🖥 Endpoint Telemetry & PowerShell Visibility

Configured enhanced PowerShell logging via GPO:

Script Block Logging (4104)

Module Logging (4103)

PowerShell Transcription

Command-line auditing for all process creation events

Provides deep visibility into:

Script execution

Suspicious or obfuscated PowerShell commands

Living-off-the-land techniques

Privileged activity tracking

🔎 Baseline Authentication Profiling

Generated controlled normal user activity from the domain-joined client:

Interactive logons

Failed logons

Application execution

PowerShell command execution

Collected and analyzed corresponding Security Event IDs on the Domain Controller to establish a baseline for anomaly detection.

🔴 Attack Simulation & Detection Validation

Performed controlled simulations using a single client VM:

Brute-force authentication attempts (4625, 4740)

Unauthorized group membership changes (4728, 4729)

Privilege escalation scenarios (4672, 4688)

Suspicious PowerShell execution (4103, 4104)

Abnormal Kerberos ticket activity (4768, 4769)

All simulations were validated against Windows Security logs to confirm detection visibility.

🛡 Hardening & Remediation

Implemented enterprise-style security hardening:

Enforced strong account and password policies

Hardened client VM and Domain Controller: disabled unnecessary services, enforced firewall, limited admin access

Secured PowerShell execution and logging

Validated that all detection logs persist across reboots

Documented configurations for mini SOC workflows

🧠 Skills Demonstrated

Active Directory Administration

Domain controller deployment

OU design and structure

User and group lifecycle management

Security Monitoring & Detection

Windows Security Event analysis

Authentication log investigation

Privilege escalation monitoring

Process execution tracking

Group Policy Engineering

Advanced audit policy configuration

Password & lockout policy enforcement

PowerShell logging configuration

Detection validation through simulation

Baseline behavior profiling

Security telemetry enhancement

Log-driven investigation workflow

🚀 Why This Project Matters

This lab demonstrates hands-on experience with:

Enterprise Windows authentication flow

How attackers generate detectable artifacts

How defenders configure visibility

How security logs support investigation and response

It reflects practical SOC-ready skills in:

Log analysis

Authentication monitoring

Security hardening

Detection engineering fundamentals
