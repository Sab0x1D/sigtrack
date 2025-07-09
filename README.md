# 📡 sigtrack

**IOC & Signature Tracker**  
A curated repository for mapping and organizing threat detection signatures and indicators.

---

## Purpose

- **YARA Rules** — Context mapping, rule-to-IOC alignment, and signature families  
- **Sigma Rules** — SIEM-based behavioral detection  
- **IOC Mapping** — IPs, hashes, C2s, mutexes, registry paths, and more  
- **Cross-linked** with [ghostyara](https://github.com/Sab0x1D/ghostyara) rules

Organized for red/blue/purple teams, SOC automation, CTI workflows, and malware tracebacks.

---

## Folder Structure

| Folder      | Description                                                     |
|-------------|-----------------------------------------------------------------|
| `./yara_map/` | Cross-linked indicators and behaviors per YARA rule/family     |
| `./sigma/`    | Sigma rules for log-based detection (e.g., Windows Event Log)  |
| `./ioc/`      | IOC sets, threat mappings, and ATT&CK-aligned technique notes  |

---

## Use Cases

- CTI analysts mapping adversary infrastructure and TTP chains  
- Threat hunters organizing coverage across detection layers  
- SOC teams cross-validating sandbox/EDR results  
- Signature developers maintaining indicator-to-rule traceability

---

## Repo Interoperability

This repo supports and extends:
- [`ghostyara`](https://github.com/Sab0x1D/ghostyara) — housing YARA detection rules
- Your broader threat intel or detection engineering pipeline

---

## Contributing

PRs welcome with the following:
- Verified indicators or sandbox references
- MITRE-aligned mappings
- Clean formatting and naming (prefer lowercase, kebab-case for files)

