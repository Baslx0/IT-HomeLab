# IT HomeLab

A hands-on IT home lab built to strengthen my practical IT support, Windows administration, networking, virtualization, and troubleshooting skills while preparing for entry-level IT Support / Help Desk roles.

This repository documents what I build, the issues I intentionally simulate, how I troubleshoot them, and how I verify each solution.

> **Build → Break → Troubleshoot → Fix → Verify → Document**

## Current Milestone — Active Directory Foundation

The first working milestone is complete:

- Microsoft Hyper-V on a Windows 11 Pro host
- Internal Hyper-V switch: `LAB-SW01`
- Lab subnet: `10.10.10.0/24`
- Domain Controller: `DC01` / `10.10.10.10`
- Active Directory Domain Services
- DNS
- Domain: `basilroot.local`
- NetBIOS: `BASILROOT`
- Windows 10 Education client: `CL01` / `10.10.10.20`
- Successful domain join and domain-user sign-in

DHCP is intentionally not configured yet. Static addressing is being used while the core Active Directory environment is built and validated.

## Goals

- Refresh and apply core IT support fundamentals.
- Build confidence troubleshooting Windows, hardware, network, and user-access issues.
- Practice Windows Server and Active Directory administration in a small-business-style environment.
- Develop clear technical documentation and ticket-writing habits.
- Prepare for CompTIA A+ and entry-level IT Support / Help Desk work.
- Build a public portfolio of practical, reproducible IT labs.

## Lab Platform

The primary virtualization platform is **Microsoft Hyper-V** running on a **Windows 11 Pro** host.

### Current Architecture

```text
Windows 11 Pro Host
└── Microsoft Hyper-V
    └── LAB-SW01 (Internal)
        └── 10.10.10.0/24
            ├── LAB-DC01
            │   └── DC01
            │       ├── Windows Server 2022 Datacenter Evaluation
            │       ├── 10.10.10.10
            │       ├── Active Directory Domain Services
            │       └── DNS
            │
            ├── LAB-CL01
            │   └── CL01
            │       ├── Windows 10 Education
            │       ├── 10.10.10.20
            │       ├── DNS: 10.10.10.10
            │       └── Domain: basilroot.local
            │
            └── LAB-LNX01
                └── Reserved VM — OS installation pending
```

The environment will expand only when a lab requires it.

## Repository Structure

```text
IT-HomeLab/
├── README.md
├── assets/
│   └── github/              # Curated showcase media only
├── docs/
│   ├── architecture.md
│   ├── environment.md
│   ├── network-diagram.md
│   └── network-plan.md
├── labs/
├── scenarios/
└── templates/
```

Local/raw media for LinkedIn and personal evidence is excluded from Git via `.gitignore`.

## Progress

| Area | Status |
|---|---|
| Repository foundation | ✅ Complete |
| Hyper-V foundation | ✅ Complete |
| Windows Server foundation | ✅ Complete |
| Active Directory foundation | ✅ Complete |
| DNS foundation | ✅ Complete |
| Windows Client domain join | ✅ Complete |
| DHCP | ⬜ Planned |
| Group Policy | ⬜ Planned |
| File Permissions | ⬜ Planned |
| Network Troubleshooting | ⬜ Planned |
| Windows Troubleshooting | ⬜ Planned |
| Linux | 🟡 VM reserved / OS pending |

## Documentation Standard

Every completed lab or scenario should include:

1. **Scenario** — What is being built or what issue is being simulated.
2. **Objective** — What the lab is intended to prove or practice.
3. **Environment** — Systems, VMs, OS versions, network, and services involved.
4. **Symptoms / Initial State** — What is observed before troubleshooting.
5. **Troubleshooting Process** — Steps taken and why.
6. **Root Cause** — Confirmed cause when applicable.
7. **Resolution** — The confirmed fix.
8. **Verification** — Evidence that the system works as expected.
9. **Evidence** — Curated screenshots, commands, logs, or configuration outputs when useful.
10. **Key Takeaway** — What was learned.

## Background

I am an Associate of Science in Computer and Information Technology candidate at Jubail Industrial College. I am building this lab to turn my academic foundation into consistent, documented practical skill.

## Contact

**Basil Albarazi**
X: https://x.com/Baslx0
Email: baslx0.dev@gmail.com
