# Cybersecurity Home Lab — Desktop PC

## Scope and current status

This is a **separate physical host** from the Windows/Active Directory IT HomeLab documented in the root README. It is intended for hands-on penetration-testing and defensive-security training in an isolated, authorized environment.

| Component | Host / platform | Status |
|---|---|---|
| Cybersecurity host | Desktop PC, VMware | Existing |
| Kali Linux VM | Desktop PC, VMware | Existing |
| Ubuntu Server VM | Desktop PC, VMware | Existing; Ubuntu 26.04 LTS observed |
| Windows VM | Desktop PC, VMware | Existing; exact guest version not yet verified |
| Docker Engine on Ubuntu Server | Desktop PC | Planned; not installed yet |
| DVWA container | Ubuntu Server VM | Planned |
| OWASP Juice Shop / WebGoat | Ubuntu Server VM | Optional future additions |
| Metasploitable 2 / other vulnerable VMs | VMware | Optional future additions |

**Important:** The Windows VM on the desktop is distinct from the Windows 10 Education domain client `CL01` in the laptop's Active Directory lab. The laptop host is documented as Windows 11 Pro; the desktop host OS and hardware specs have not been confirmed.

## Logical architecture (planned)

```text
Desktop PC — VMware
├── Kali Linux VM                 (security testing)
├── Ubuntu Server 26.04 LTS VM    (Docker host, planned)
│   ├── DVWA                     (planned)
│   ├── OWASP Juice Shop          (optional)
│   └── WebGoat                   (optional)
└── Windows VM                    (Windows security exercises)

VM-to-VM training traffic: dedicated isolated / host-only virtual network
Network subnet/IPs: TBD; do not reuse the laptop lab's 10.10.10.0/24 without planning
```

Containers complement the existing virtual machines; they do **not** replace Kali, Ubuntu Server, or Windows VMs. Vulnerable applications must not be exposed to the internet or to other trusted household devices. Avoid bridged adapters for deliberately vulnerable machines; use an isolated lab network and snapshots. If temporary connectivity is required for downloading images or updates, enable it only as needed and disable it afterward.

## Managing two physical labs without switching desks

**Recommended:** Keep both labs on their own physical computers, then operate them from one primary workstation using trusted remote management of the **hosts**.

- Prefer Remote Desktop for a supported Windows host, or a remote-control solution limited to the household management network; SSH works for Ubuntu administration.
- Do not attach the deliberately vulnerable **guest network** directly to the household LAN. If remote lab access is required, manage the hypervisor/host through a separately controlled management path.
- For access away from home, consider a private VPN with MFA and restrictive access controls; never forward RDP, SSH, or intentionally vulnerable service ports publicly.
- Store instructions, diagrams, and evidence in GitHub while excluding credentials, tokens, and sensitive lab data.

## Next steps

1. Verify desktop host OS, CPU, RAM, VMware edition, guest OS versions, and current virtual network settings.
2. Create/verify a dedicated isolated VMware virtual network for testing.
3. Take VM snapshots.
4. Install Docker Engine and Compose on the existing Ubuntu Server VM.
5. Deploy DVWA only on the isolated lab network; verify Kali can reach it without internet exposure.
6. Document tested IPs and add screenshots/evidence only after verified.

## Documentation status

This document captures the architecture and intended additions described during planning. Docker, DVWA, and other intentionally vulnerable targets are **not** being claimed as deployed.
