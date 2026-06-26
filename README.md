# SC-200 Measured Skills Revision Guide
Microsoft Certified: Security Operations Analyst Associate Revision Guide

| SC-200 | Detail |
| --- | --- |
| Purpose | A bullet-by-bullet revision guide mapped to the SC-200 measured skills list supplied by the candidate. It is designed for efficient exam recall, not as a replacement for hands-on labs. |
| How to use it | Read each objective, test whether you can explain the configuration path and operational purpose, then use the cram version for last-pass revision. |
| Exam mindset | SC-200 usually tests which Microsoft security capability, table, rule type, connector, portal workflow, or response action fits a scenario. |
| Source basis | Compiled from the Microsoft Learn online course. Verify the official skills outline again immediately before booking the exam, as Microsoft exam objectives can change. |

## Revision map
- Manage a security operations environment: configuration, automation, Sentinel platform, ingestion, detections.
- Respond to security incidents: Defender XDR and Sentinel incident handling, workload-specific investigations, Purview and Microsoft 365 activity investigation.
- Perform threat hunting: KQL, advanced hunting, Sentinel hunting, graph-based investigation, notebooks, data lake and summary tables.

# Manage a security operations environment (40-45%)
## Configure automation for Microsoft Defender XDR and Microsoft Sentinel
**Configure email notifications in Microsoft Defender XDR, including incidents, actions, and threat analytics**
| SC-200 | Detail |
| --- | --- |
| What this means | Know how Defender XDR notifies analysts or SOC distribution groups when incidents are created or updated, when response actions occur, and when threat analytics reports are published or updated. |
| Portal / path | Microsoft Defender portal > Settings > Microsoft Defender XDR > Email notifications. Use the Incidents, Actions, and Threat analytics areas as applicable. |

**What to know for the exam**
- ncident notifications are for correlated attack cases, not for creating detections.
- Action notifications relate to remediation or response activity such as AIR, isolation, quarantine, Live Response actions, and email remediation.
- Threat Analytics notifications are intelligence-led notifications about campaigns, exposure, and recommended mitigations.
- Recipients are normally SOC mailboxes, duty analyst groups, IR groups, or security management distribution lists.
  
**Key distinctions**
- Incident notification = attack case awareness. Action notification = remediation activity awareness. Threat Analytics notification = intelligence awareness.
- Defender XDR email notifications are not Sentinel playbooks or automation rules.
  
**Likely exam traps**
- Do not choose an analytics rule when the task only asks to email someone about an existing Defender XDR incident.
- Do not confuse Threat Analytics notifications with threat intelligence indicator ingestion.
| SC-200 | Detail |
| --- | --- |
| Cram version | Incidents = attack cases. Actions = response/remediation. Threat Analytics = Microsoft threat intelligence updates. |

## Configure alert notifications in Microsoft Defender XDR, including tuning, suppression, and correlation
