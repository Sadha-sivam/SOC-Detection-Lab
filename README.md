# SOC Detection Lab — Purple Team Detection Engineering

> A hands-on SOC lab where I **emulate adversary techniques**, **engineer and validate security detections** mapped to **MITRE ATT&CK**, and **document detection coverage** across the complete detection engineering lifecycle.

**Author:** Sadhasivam  
**GitHub:** [Sadha-sivam](https://github.com/Sadha-sivam)  
**Stack:** Wazuh (SIEM) · Sysmon · auditd · Sigma · Atomic Red Team · MITRE ATT&CK Navigator

![Status](https://img.shields.io/badge/status-in%20progress-orange)
![Focus](https://img.shields.io/badge/focus-detection%20engineering-blue)
![Framework](https://img.shields.io/badge/mapped%20to-MITRE%20ATT%26CK-red)

---

## 🎯 Goal

Build a functional SOC environment, simulate realistic adversary techniques, and answer an important security operations question:

**"Can I detect this activity and prove it with security evidence?"**

Every emulated technique follows a detection engineering workflow:

- Detection rule development
- Security event analysis
- Detection validation
- MITRE ATT&CK mapping
- Investigation documentation for chained attack scenarios

## 🧩 Architecture

```text
Attacker (Kali + Atomic Red Team / Caldera)
              |
              | Executes ATT&CK techniques
              v
Victim Endpoints
    Windows (Sysmon)
    Linux   (auditd)
              |
              | Security telemetry
              v
       Wazuh Agents
              |
              v
       Wazuh SIEM
    (Indexer + Dashboard)
              |
       +------+------+
       |      |      |
       v      v      v
   Detection Alerts  Threat
    Rules            Hunting
       |
       v
 Investigation and Incident Response
       |
       v
 ATT&CK Coverage and Documentation
```

See `docs/lab-architecture.md` for the lab topology and `lab/README.md` for setup instructions.

## 🗺️ Roadmap

| Phase | Objective | Deliverable |
|---|---|---|
| 1. Lab & Telemetry | Configure Wazuh, agents, Sysmon and auditd | Validated lab setup |
| 2. Baseline & Dashboards | Establish monitoring and reduce unnecessary alerts | Dashboard exports |
| 3. Adversary Emulation | Execute MITRE ATT&CK techniques | Emulation plans and results |
| 4. Detection Engineering | Develop and validate Sigma rules | Detection rules |
| 5. Threat Hunting | Investigate suspicious activity and behavioral patterns | Hunting reports |
| 6. Investigation & IR | Investigate chained attack scenarios and document response | Investigation reports and playbooks |

## 📁 Repository Structure

```text
SOC-Detection-Lab/
├── lab/                 # SOC lab setup and configuration
├── detections/
│   └── sigma/           # Sigma detection rules
├── emulation/           # Adversary emulation plans and results
├── playbooks/           # Incident response playbooks
├── investigations/      # Security investigation reports
└── docs/                # Architecture and ATT&CK coverage
```

## 🛡️ Detection Scenarios

| Detection | MITRE ATT&CK | Telemetry Source | Status |
|---|---|---|---|
| PowerShell encoded command | T1059.001 | Sysmon EID 1 | ✅ Validated |
| LSASS access (credential dumping) | T1003.001 | Sysmon EID 10 | ✅ Validated |
| Registry Run key persistence | T1547.001 | Sysmon EID 13 | ✅ Validated |
| Scheduled task creation | T1053.005 | Sysmon EID 1 | ✅ Validated |
| Local account creation | T1136.001 | Sysmon EID 1 | ✅ Validated |
| Windows event log clearing | T1070.001 | Sysmon EID 1 | ✅ Validated |
| Ingress tool transfer (certutil) | T1105 | Sysmon EID 1 | 🟡 Blocked by Defender in this lab |

### Scenario Validation

The documented `scenario-01` chained intrusion exercise recorded:

- 6 out of 7 techniques detected.
- 3 detection rules corrected during validation.
- Investigation findings documented.

See `investigations/2026-08-23-scenario-01-chained-intrusion.md` for the investigation details.

See `docs/attack-coverage.md` for the ATT&CK coverage matrix.

## 🧠 Skills Demonstrated

`SOC Operations` · `Wazuh SIEM` · `Detection Engineering` · `Sysmon` · `Linux auditd` · `Sigma Rules` · `MITRE ATT&CK` · `Atomic Red Team` · `Adversary Emulation` · `Threat Hunting` · `Incident Investigation` · `Incident Response`

---

## ⚠️ Security Notice

This project is intended for cybersecurity research, education, and defensive security testing.

All offensive techniques are executed in an isolated, authorized lab environment on systems controlled by the lab operator, with the objective of developing and validating defensive detections.
