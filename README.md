# SC-200 Measured Skills Revision Guide
Microsoft Certified: Security Operations Analyst Associate

| SC-200 | Detail |
| --- | --- |
| Purpose | A bullet-by-bullet revision guide mapped to the SC-200 measured skills list. It is designed for efficient exam recall, not as a replacement for hands-on labs or training. |
| How to use it | Read each objective, test whether you can explain the configuration path and operational purpose, then use the cram version for last-pass revision. |
| Exam mindset | SC-200 usually tests which Microsoft security capability, table, rule type, connector, portal workflow, or response action fits a scenario. |
| Source basis | Compiled from the Microsoft Learn course. Verify the official skills outline again immediately before booking the exam, as Microsoft exam objectives can change. |

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

- Incident notifications are for correlated attack cases, not for creating detections.
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

**Configure alert notifications in Microsoft Defender XDR, including tuning, suppression, and correlation**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how alert email notifications differ from incident notifications, and how Defender XDR reduces noise through alert tuning and correlation. |
| Portal / path | Microsoft Defender portal > Settings > Microsoft Defender XDR > Email notifications > Alerts. Alert tuning is under Settings > Microsoft Defender XDR > Alert tuning, and can also be started from an alert in many workflows. |

**What to know for the exam**

- Alert notifications email recipients when new alerts are created, typically filtered by severity, source, scope, or device group.
- Alert tuning suppresses or auto-resolves known benign alert patterns.
- Suppression should be carefully scoped: device-specific suppression is safer than tenant-wide suppression.
- Correlation groups related alerts from endpoint, identity, email, cloud apps, and other Defender workloads into an incident.

**Key distinctions**

- Alert = detection signal. Incident = correlated attack story.
- Tuning reduces noise; custom detections create new alert logic.
- Defender XDR correlation is not the same as Sentinel analytics rule correlation.

**Likely exam traps**

- Do not suppress alerts broadly unless the scenario clearly says the activity is known, benign, and repeatable.
- Do not pick Sentinel automation rules when the task is specifically Defender XDR alert notification/tuning.

| SC-200 | Detail |
| --- | --- |
| Cram version | Alert notifications = detection emails. Tuning/suppression = reduce benign noise. Correlation = many related alerts become one incident. |

**Configure Microsoft Defender for Endpoint advanced features**

| SC-200 | Detail |
| --- | --- |
| What this means | Understand the Defender for Endpoint tenant-level advanced features that enable deeper endpoint protection, integration, preview capabilities, EDR block mode, Live Response, telemetry sharing, and cross-product workflows. |
| Portal / path | Microsoft Defender portal > Settings > Endpoints > Advanced features. |

**What to know for the exam**

- Advanced features are tenant settings that can enable or disable endpoint capabilities across the Defender for Endpoint service.
- Common examples include automated investigation, Live Response, EDR in block mode, endpoint detection and response integration, Microsoft Intune connection, web content filtering, custom network indicators, and preview features.
- Some features require licensing, onboarding state, sensor health, or integration with Intune or Defender XDR.
- Changes can affect operational capability, so know whether a feature is detection, response, integration, or preview-related.

**Key distinctions**

- Advanced features are service-wide capability toggles; endpoint security policies are configuration profiles/rules applied to devices.
- Live Response is interactive response on a device; AIR is automated investigation and remediation.

**Likely exam traps**

- Do not confuse Advanced features with ASR rules. ASR rules are endpoint security controls, often deployed through Intune, GPO, or security settings management.
- If a question asks to enable MDE integration with Intune, think Advanced features and tenant settings, not a KQL rule.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDE advanced features = tenant capability switches for endpoint response, integration, and enhanced protection. |

**Configure rules settings in Microsoft Defender for Endpoint**

| SC-200 | Detail |
| --- | --- |
| What this means | Know the rule-setting concepts used to control endpoint detections, indicators, web filtering, automation, and attack surface reduction behaviour. |
| Portal / path | Microsoft Defender portal > Settings > Endpoints. Some rule settings are managed through Indicators, Web content filtering, Device groups, Advanced features, or Security settings management; ASR policy is commonly managed in Intune Endpoint security. |

**What to know for the exam**

- Rules may control allow/block indicators for files, certificates, IPs, URLs, and domains.
- Web content filtering uses categories and scoped policies to block or audit web access.
- Automation levels may be scoped through device groups.
- Endpoint security rules such as ASR can be deployed through Intune, Configuration Manager, Group Policy, PowerShell, or security settings management depending on architecture.

**Key distinctions**

- Indicators are IOC-based allow/block decisions. ASR rules are behavioural prevention controls. Alert suppression/tuning is about alert noise, not endpoint control.
- MDE rules are not Sentinel analytics rules.

**Likely exam traps**

- If the scenario says block a hash, URL, IP, or certificate on endpoints, think MDE indicators, not Sentinel watchlists.
- If the scenario says reduce specific alert noise, think alert tuning/suppression rather than ASR.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDE rule settings can mean indicators, web filtering, automation scope, or endpoint security controls. Match the rule type to the task. |

**Configure custom data collection in Microsoft Defender for Endpoint**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how MDE can collect additional endpoint evidence for investigation, hunting, and response, especially through device telemetry, investigation packages, Live Response, and custom collection packages. |
| Portal / path | Microsoft Defender portal > Assets > Devices > device page > response actions, or Settings > Endpoints for collection-related features. Advanced hunting uses collected endpoint telemetry in tables such as DeviceProcessEvents, DeviceFileEvents, DeviceNetworkEvents, DeviceRegistryEvents, DeviceEvents, and DeviceInfo. |

**What to know for the exam**

- MDE collects rich endpoint telemetry automatically after onboarding.
- Analysts can collect an investigation package from a device for deeper triage.
- Live Response can be used to run commands, collect files, and perform investigation actions on supported devices.
- Advanced hunting exposes MDE endpoint telemetry through schema tables.
- Custom detection rules can use advanced hunting query results and trigger actions on devices or files.

**Key distinctions**

- Collect investigation package = gather forensic-style endpoint data. Advanced hunting = query telemetry. Custom detection = operationalize a KQL query as recurring detection logic.
- MDE custom data collection is different from Sentinel data connector ingestion.

**Likely exam traps**

- Do not choose Sentinel AMA data collection rules when the requirement is specifically to collect endpoint evidence through MDE.
- Do not confuse collecting an investigation package with isolating a device.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDE custom collection = endpoint evidence and telemetry for investigation; hunting tables expose the data. |

**Configure security policies for Microsoft Defender for Endpoint, including attack surface reduction (ASR) rules**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how endpoint protection policies are configured and deployed, especially ASR rules that reduce common malware and attacker behaviours. |
| Portal / path | Common path: Microsoft Intune admin center > Endpoint security > Attack surface reduction. In Defender portal, use Endpoints > Configuration management / Security settings management where applicable. |

**What to know for the exam**

- ASR rules can block or audit risky behaviours such as Office child process creation, credential stealing from LSASS, executable content from email/webmail, script abuse, and vulnerable driver abuse.
- ASR can be deployed in Audit, Warn, or Block modes depending on rule and policy design.
- Policies can be scoped to device groups or Entra groups depending on management channel.
- Use audit mode to assess impact before enforcing broadly in production.
- Exclusions should be specific and justified.

**Key distinctions**

- ASR is prevention/hardening. MDE alerts are detection. AIR is response. Secure Score recommendations may suggest enabling ASR rules but do not deploy them by themselves.
- Intune endpoint security policy is usually the management plane for modern Windows endpoints.

**Likely exam traps**

- Do not select Safe Attachments or Safe Links for endpoint ASR questions; those are Defender for Office 365 controls.
- Do not use Sentinel analytics rules to enforce endpoint security settings.

| SC-200 | Detail |
| --- | --- |
| Cram version | ASR = endpoint hardening rules that block common attack behaviours. Deploy carefully, test in audit/warn, then enforce. |

**Manage automated investigation and response capabilities in Microsoft Defender XDR**

| SC-200 | Detail |
| --- | --- |
| What this means | Understand AIR: automated investigations, evidence verdicts, pending actions, remediation actions, and Action Center review. |
| Portal / path | Microsoft Defender portal > Incidents & alerts > Incidents / Alerts / Investigations, and Action center for pending and completed remediation actions. |

**What to know for the exam**

- AIR starts from alerts or playbooks and investigates related entities such as files, processes, devices, users, URLs, and emails.
- Evidence verdicts include Malicious, Suspicious, and No threats found.
- Remediation may be automatic or require approval depending on automation level and policy.
- Action Center shows pending actions and history across devices, email/collaboration, and identities.
- Completed actions may sometimes be undone, such as device isolation or file quarantine.

**Key distinctions**

- AIR = Microsoft automated investigation/remediation. Sentinel playbook = Logic Apps-based SOAR. Automatic attack disruption = high-confidence containment across entities.
- Pending actions require analyst approval; history is the audit trail.

**Likely exam traps**

- Do not assume every AIR remediation is automatic; automation level matters.
- Do not confuse resolving an alert with fully remediating all entities in an incident.

| SC-200 | Detail |
| --- | --- |
| Cram version | AIR investigates evidence, assigns verdicts, proposes or performs remediation, and records actions in Action Center. |

**Configure automatic attack disruption in Microsoft Defender XDR**

| SC-200 | Detail |
| --- | --- |
| What this means | Know that automatic attack disruption is high-confidence, cross-domain containment designed to stop active attacks quickly by taking actions on compromised users and devices. |
| Portal / path | Microsoft Defender portal > Settings > Microsoft Defender XDR / Endpoints / Identities areas depending on feature availability and workload prerequisites. Investigation occurs in incident pages and Action Center. |

**What to know for the exam**

- Automatic attack disruption uses Defender XDR correlation and high-confidence signals to contain active attacks.
- Actions may include device containment/isolation and account containment actions such as disabling a user or revoking sessions depending on scenario and permissions.
- It is intended for severe multi-stage attacks such as ransomware, business email compromise, adversary-in-the-middle, and lateral movement.
- Actions are visible in the incident and Action Center.

**Key distinctions**

- Attack disruption is not the same as basic alert suppression or a Sentinel playbook. It is built-in Defender XDR response driven by correlated high-confidence attack evidence.
- Prerequisites vary by workload, licensing, onboarding, and RBAC permissions.

**Likely exam traps**

- Do not use attack disruption for ordinary low-confidence noise. It is meant to interrupt active attacks.
- Do not assume Sentinel must be present; attack disruption is a Defender XDR capability.

| SC-200 | Detail |
| --- | --- |
| Cram version | Automatic attack disruption = built-in high-confidence containment of active cross-domain attacks. |

**Configure and manage device groups, permissions, and automation levels in Microsoft Defender for Endpoint**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how MDE device groups control scope, RBAC visibility, automation levels, and sometimes policy targeting. |
| Portal / path | Microsoft Defender portal > Settings > Endpoints > Permissions > Device groups / Roles, and Settings > Endpoints > Advanced features / automation settings as applicable. |

**What to know for the exam**

- Device groups can be based on tags, domains, OS, or other device attributes depending on configuration.
- They are used to scope what analysts can see and manage.
- Device groups can define automation level, such as full automation or semi-automation.
- RBAC roles determine whether users can view data, manage alerts, perform Live Response, collect files, or perform remediation.
- Least privilege is important; Global Administrator should not be the routine SOC role.

**Key distinctions**

- Device group = scope. RBAC role = permission. Automation level = how much remediation can occur automatically.
- Defender XDR unified RBAC may replace or align separate workload permissions.

**Likely exam traps**

- Do not confuse Entra groups with MDE device groups. They can both be used in security operations, but they are different constructs.
- If a question says one analyst should only manage a subset of endpoints, think device groups plus RBAC scope.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDE device groups define scope; permissions define authority; automation levels define remediation behaviour. |

**Create and configure automation rules in Microsoft Sentinel**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Sentinel automation rules run when incidents or alerts are created/updated and can assign, tag, change severity/status, or run playbooks. |
| Portal / path | Microsoft Sentinel > Automation > Automation rules. |

**What to know for the exam**

- Automation rules operate at the Sentinel incident/alert workflow level.
- They can set owner, status, severity, tags, and trigger playbooks.
- They support conditions such as analytics rule name, incident provider, severity, entities, or tactics depending on current portal capability.
- Rule order matters when multiple automation rules match.
- They are useful for triage routing, enrichment kickoff, notifications, and repeatable SOC handling.

**Key distinctions**

- Automation rule = native Sentinel workflow control. Playbook = Logic App that performs actions/integrations.
- Analytics rule = creates detections/incidents. Automation rule = acts after a match/event occurs.

**Likely exam traps**

- Do not select a playbook alone when the requirement is to trigger it automatically based on incident criteria; use an automation rule to run the playbook.
- Do not confuse automation rules with KQL scheduled analytics rules.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel automation rules act on incidents/alerts and can launch playbooks; they do not query raw logs themselves. |

**Create and configure Microsoft Sentinel playbooks**

| SC-200 | Detail |
| --- | --- |
| What this means | Know that Sentinel playbooks are Azure Logic Apps used for SOAR actions such as enrichment, notification, ticketing, containment, and evidence gathering. |
| Portal / path | Microsoft Sentinel > Automation > Playbooks, or Azure Logic Apps. Trigger commonly comes from a Sentinel automation rule. |

**What to know for the exam**

- Playbooks are Logic Apps workflows connected to Microsoft Sentinel.
- Common triggers include incident, alert, or entity trigger depending on template and connector.
- Typical actions include sending Teams/email notifications, creating ServiceNow/Jira tickets, enriching IPs/domains/hashes, disabling users, blocking indicators, or updating incidents.
- Playbooks require managed identity or service connection permissions.
- Use automation rules to run playbooks automatically when matching incident criteria are met.

**Key distinctions**

- Playbook = workflow engine. Automation rule = trigger and routing logic. Analytic rule = detection logic.
- Logic Apps consumption costs and permissions matter in production.

**Likely exam traps**

- Do not pick a workbook when the task asks to automate response; workbooks visualize data only.
- Do not forget permissions: a playbook cannot disable a user or isolate a device unless its identity/connection has rights.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel playbooks = Logic Apps SOAR. Use automation rules to trigger them from incidents/alerts. |

## Configure the Microsoft Sentinel SIEM and platform

**Specify Microsoft Sentinel roles**

| SC-200 | Detail |
| --- | --- |
| What this means | Know the built-in Azure RBAC roles used to grant access to Sentinel workspaces and operational tasks. |
| Portal / path | Azure portal > Resource group / Log Analytics workspace / Microsoft Sentinel > Access control (IAM). Sentinel also appears in the Defender portal experience in newer deployments. |

**What to know for the exam**

- Microsoft Sentinel Reader can view incidents, data, workbooks, and other resources but cannot make changes.
- Microsoft Sentinel Responder can manage incidents, such as assign, update status, and add comments.
- Microsoft Sentinel Contributor can create and edit analytics rules, workbooks, hunting queries, automation rules, and other Sentinel resources.
- Microsoft Sentinel Playbook Operator can run playbooks manually.
- Microsoft Sentinel Automation Contributor allows automation rules to run playbooks. Additional Azure roles may be needed for Logic Apps, Log Analytics, or resource changes.

**Key distinctions**

- Sentinel roles are Azure RBAC roles. Defender XDR unified RBAC is a different permissions model.
- Reader/Responder/Contributor map broadly to view/respond/configure.

**Likely exam traps**

- If a user can see but cannot change incidents, Reader is likely enough. If they need to update incidents, use Responder. If they need to build rules, use Contributor.
- Do not grant Owner/Contributor at subscription scope when Sentinel-specific roles are sufficient.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel Reader = view. Responder = manage incidents. Contributor = configure Sentinel. Playbook Operator = run playbooks. |

**Manage data retention for XDR and Microsoft Sentinel tables, including Analytics, Data lake, and XDR tiers**

| SC-200 | Detail |
| --- | --- |
| What this means | Understand retention choices across Sentinel/Log Analytics analytics tables, lower-cost retention tiers, data lake capabilities, and Defender XDR hunting retention. |
| Portal / path | Microsoft Sentinel / Log Analytics workspace > Tables > Manage table plan and retention. Defender XDR hunting data and Sentinel data lake are managed in their respective platform settings. |

**What to know for the exam**

- Analytics tier supports full query and analytics rule use cases in Log Analytics.
- Long-term retention/archive can reduce cost for older data but may require search jobs or restoration before full analytics.
- Data lake capabilities support large-scale retention and investigation scenarios in the modern Sentinel platform.
- Defender XDR advanced hunting has its own retention model, commonly shorter than SIEM retention unless data is streamed or stored elsewhere.
- Retention must balance compliance, investigation value, query performance, and cost.

**Key distinctions**

- Analytics tables are for active detection and fast query. Archive/long-term retention is for cheaper storage and investigation retrieval. XDR hunting retention is not the same as Sentinel workspace retention.
- Data retention does not equal data ingestion; connector choice controls what arrives.

**Likely exam traps**

- Do not assume Defender XDR stores raw hunting data for the same duration as Sentinel.
- Do not put all data into high-cost Analytics tier if only long-term compliance search is needed.

| SC-200 | Detail |
| --- | --- |
| Cram version | Retention = how long data stays and in what tier. Analytics = active SIEM use. Archive/Data lake = longer/cheaper or large-scale investigation. XDR has separate retention. |

**Create and configure Microsoft Sentinel workbooks**

| SC-200 | Detail |
| --- | --- |
| What this means | Know that workbooks are interactive dashboards and reports for visualising Sentinel and Log Analytics data. |
| Portal / path | Microsoft Sentinel > Threat management / Workbooks, or Azure Monitor > Workbooks. |

**What to know for the exam**

- Workbooks use KQL queries and visual components such as grids, charts, parameters, and markdown.
- They are useful for SOC dashboards, operational reporting, connector health, incident trends, and hunting visualisation.
- They do not create alerts or incidents.
- They can be based on built-in templates or custom-built.
- Permissions are needed to read the underlying workspace data.

**Key distinctions**

- Workbook = visualisation/report. Analytics rule = detection. Playbook = automated action. Watchlist = reference data.
- A workbook can show detection coverage but cannot enforce response.

**Likely exam traps**

- If the scenario asks for a dashboard, use a workbook. If it asks to trigger an alert, use an analytics rule.
- Do not confuse workbook parameters with automation rule conditions.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel workbooks = interactive KQL dashboards. They visualise; they do not detect or remediate. |

**Optimize the Microsoft Sentinel platform, including SOC optimization recommendations**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Sentinel helps improve detection coverage, reduce noise, optimize cost, and improve SOC processes through recommendations and operational insights. |
| Portal / path | Microsoft Sentinel > SOC optimization / Content hub / Analytics / Data connectors / Workbooks, depending on recommendation type. |

**What to know for the exam**

- SOC optimization recommendations may suggest enabling analytics rules, ingesting missing data sources, improving MITRE coverage, addressing noisy rules, or tuning false positives.
- Optimization also includes cost management: table plans, retention, filtering, DCRs, and avoiding unnecessary ingestion.
- Content hub solutions deploy connectors, rules, workbooks, parsers, hunting queries, and playbooks for specific products or scenarios.
- Use MITRE ATT&CK coverage to identify detection gaps.

**Key distinctions**

- SOC optimization = improve operational effectiveness. Cost optimization = reduce ingestion/storage spend. They overlap but are not identical.
- Content hub installs content; analytics rules must still be reviewed, enabled, and tuned.

**Likely exam traps**

- Do not enable every rule without tuning; high false positives damage SOC effectiveness.
- Do not treat recommendations as mandatory without considering data availability and business risk.

| SC-200 | Detail |
| --- | --- |
| Cram version | Optimize Sentinel by improving coverage, reducing noise, controlling cost, and using SOC optimization/content recommendations. |

## Ingest data into the Microsoft Sentinel SIEM and platform

**Select data connectors based on data source requirements, including Windows logs and security events**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how to choose Sentinel connectors based on where data originates, what format it uses, and whether the source is cloud-native, agent-based, syslog, CEF, API, or custom. |
| Portal / path | Microsoft Sentinel > Content management > Content hub, and Microsoft Sentinel > Data connectors. |

**What to know for the exam**

- Use Microsoft-native connectors for Entra ID, Microsoft 365, Defender XDR, Azure Activity, Defender for Cloud, and other Microsoft services.
- Use Windows Security Events via AMA for Windows event collection into Log Analytics.
- Use Syslog via AMA for Linux/syslog sources and CEF via AMA for appliances that output Common Event Format.
- Use API-based connectors for SaaS and vendor integrations where available.
- Use custom logs/tables where no built-in connector exists.

**Key distinctions**

- Connector = ingestion mechanism. Analytics rule = detection. Workbook = visualisation. Parser = normalises/query-shapes data.
- AMA/DCR is modern Azure Monitor collection; legacy agents/connectors may still appear in older material.

**Likely exam traps**

- Do not use Syslog connector for native Windows Security Event collection.
- Do not assume all connectors create incidents; many only ingest data.

| SC-200 | Detail |
| --- | --- |
| Cram version | Pick connectors by source and format: Microsoft native/API, Windows via AMA, Linux/appliances via Syslog/CEF AMA, custom logs for unsupported sources. |

**Configure collection of Windows Security events by using Windows Security Events via AMA, including data collection rules**

| SC-200 | Detail |
| --- | --- |
| What this means | Know the modern AMA-based method for collecting Windows Security Events into Sentinel using Data Collection Rules. |
| Portal / path | Microsoft Sentinel > Data connectors > Windows Security Events via AMA. Configure a Data Collection Rule and associate it with machines or Azure Arc-enabled servers. |

**What to know for the exam**

- AMA is the modern agent for Windows event collection.
- Data Collection Rules define which events/facilities are collected and where data is sent.
- Machines must be Azure VMs or Azure Arc-enabled servers for central management.
- You can select event sets such as All Security Events, Common, Minimal, or custom XPath queries depending on connector capability.
- Collected data lands in SecurityEvent or related tables depending on configuration.

**Key distinctions**

- AMA replaces older Log Analytics/MMA approaches for many scenarios. DCR controls collection; analytics rules query the collected table.
- WEF can forward events to collectors; AMA can then collect from the collector depending on design.

**Likely exam traps**

- If the requirement is specific Windows event selection, think DCR/XPath rather than Sentinel analytics rule.
- Do not confuse Microsoft Security Events connector with Defender for Endpoint telemetry.

| SC-200 | Detail |
| --- | --- |
| Cram version | Windows Security Events via AMA = agent + DCR + target machines + selected events into Sentinel. |

**Plan and configure collection of Windows Security events by using Windows Event Forwarding (WEF)**

| SC-200 | Detail |
| --- | --- |
| What this means | Know when to use Windows Event Forwarding architecture to centralise Windows events before sending to Sentinel. |
| Portal / path | Configure WEF on Windows Event Collector servers using subscriptions/GPO; then collect from the collector using AMA/Sentinel design. |

**What to know for the exam**

- WEF uses Windows-native event forwarding from source computers to collector servers.
- It is useful for environments where installing/connecting every endpoint directly is not desirable.
- Collectors need capacity planning, subscription design, and event filtering.
- Use source-initiated subscriptions for scale.
- Sentinel ingestion still requires a supported path from the collector to Log Analytics/Sentinel.

**Key distinctions**

- WEF = Windows event aggregation architecture. AMA = Azure Monitor collection agent. Sentinel connector = ingestion configuration.
- WEF does not by itself put data into Sentinel.

**Likely exam traps**

- Do not pick WEF when the source is Linux Syslog or a firewall appliance.
- Do not collect every Windows event without filtering; cost and noise can explode.

| SC-200 | Detail |
| --- | --- |
| Cram version | WEF forwards Windows events to collectors; Sentinel still needs AMA/connector ingestion from the collector path. |

**Plan and configure Syslog via AMA and Common Event Format (CEF) via AMA connectors**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Sentinel ingests Linux/syslog and CEF appliance data using AMA and a Linux collector/forwarder. |
| Portal / path | Microsoft Sentinel > Data connectors > Syslog via AMA or Common Event Format (CEF) via AMA. Configure DCR and Linux collector/forwarder. |

**What to know for the exam**

- Syslog via AMA collects standard syslog facilities/severities from Linux systems and network devices.
- CEF via AMA is used for security appliances and products that emit Common Event Format.
- A Linux collector or forwarding host is commonly used to receive syslog/CEF and send it to Log Analytics through AMA.
- DCRs control which facilities/severities/log streams are collected.
- CEF parsing normalises vendor events into a security-friendly schema.

**Key distinctions**

- Syslog is a transport/log format. CEF is a structured security event format over syslog. AMA is the collection agent.
- CEF is often preferred for SIEM appliance logs when supported by the vendor.

**Likely exam traps**

- Do not use CEF just because the source is a firewall; the device must actually output CEF or a supported transformation path must exist.
- Do not forget network prerequisites: devices must forward to the collector over the configured syslog port.

| SC-200 | Detail |
| --- | --- |
| Cram version | Syslog via AMA = generic syslog. CEF via AMA = structured security appliance logs. Both typically need a Linux collector and DCR. |

**Configure collection of Azure activities by using Azure Policy and resource diagnostic settings**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Azure platform logs and resource logs are sent to Sentinel/Log Analytics through diagnostic settings, often deployed at scale with Azure Policy. |
| Portal / path | Azure resource / subscription > Diagnostic settings, or Azure Policy initiatives to deploy diagnostic settings to Log Analytics. Sentinel then queries the destination tables. |

**What to know for the exam**

- Azure Activity logs record subscription-level control-plane operations.
- Resource diagnostic settings send resource logs and metrics to Log Analytics, Event Hub, or Storage.
- Azure Policy can enforce or deploy diagnostic settings at scale across resources.
- Different Azure resources produce different log categories and tables.
- Use diagnostic settings when you need Azure service logs for detection, investigation, and compliance.

**Key distinctions**

- Azure Activity = control-plane subscription operations. Resource logs = service-specific logs. Policy = scale/standardisation mechanism.
- Defender for Cloud alerts are different from raw Azure diagnostic logs.

**Likely exam traps**

- Do not assume enabling Sentinel automatically collects every Azure resource log. Diagnostic settings are often required.
- Do not send logs to Storage only if Sentinel analytics must query them directly.

| SC-200 | Detail |
| --- | --- |
| Cram version | Azure logs to Sentinel usually need diagnostic settings; Azure Policy deploys them consistently at scale. |

**Ingest threat indicators into Microsoft Sentinel**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how threat intelligence indicators are imported into Sentinel and used for matching, hunting, and analytics. |
| Portal / path | Microsoft Sentinel > Threat intelligence, Data connectors > Threat Intelligence platforms / TAXII / Microsoft Defender Threat Intelligence depending on source. |

**What to know for the exam**

- Threat indicators can include IPs, domains, URLs, file hashes, and other STIX-style indicators.
- Sentinel can ingest indicators from TAXII feeds, threat intelligence platforms, Microsoft threat intelligence, or manual/API sources.
- Indicators are queried in ThreatIntelligenceIndicator or newer related tables depending on connector/version.
- Threat intelligence analytics rules can match indicators against log data.
- Indicator freshness, confidence, expiration, and source quality matter.

**Key distinctions**

- Threat indicators = intelligence objects. Analytics rules = logic that matches indicators to events. Watchlists = customer reference data, not necessarily threat intelligence.
- Defender XDR has native Microsoft threat intelligence; Sentinel ingestion still depends on connectors/content.

**Likely exam traps**

- Do not treat every indicator match as automatically malicious; context and confidence matter.
- Do not confuse MDTI reports/analytics with IOC ingestion into Sentinel tables.

| SC-200 | Detail |
| --- | --- |
| Cram version | Threat intel ingestion brings IOCs into Sentinel; analytics/hunting uses them to find matches in logs. |

**Create custom log tables in the workspace to store ingested data**

| SC-200 | Detail |
| --- | --- |
| What this means | Know when and how custom tables are used for unsupported or custom data sources in Log Analytics/Sentinel. |
| Portal / path | Log Analytics workspace > Tables, Data Collection Endpoints/Data Collection Rules, or custom log ingestion API depending on architecture. |

**What to know for the exam**

- Custom tables usually have names ending in _CL or use modern custom table schemas depending on ingestion path.
- They store data that does not fit a built-in connector or table.
- You must define columns/schema, ingestion method, and transformation where needed.
- KQL analytics, workbooks, and hunting queries can use custom tables once data is available.
- Custom tables may need parsing or normalisation to align with ASIM or SOC query patterns.

**Key distinctions**

- Custom table = storage/schema. Custom connector/ingestion pipeline = how data arrives. Parser/ASIM = query normalisation.
- Creating a custom table does not automatically create detections.

**Likely exam traps**

- Do not use custom logs when a supported connector already provides normalised data unless there is a clear requirement.
- Do not forget table retention and cost implications.

| SC-200 | Detail |
| --- | --- |
| Cram version | Custom log tables store unsupported/custom ingested data; then build parsers, analytics, workbooks, or hunting queries over them. |

## Configure detections

**Create custom detection rules by using Advanced Hunting in Microsoft Defender XDR**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how to turn an advanced hunting KQL query into a recurring Defender XDR custom detection rule. |
| Portal / path | Microsoft Defender portal > Investigation & response > Hunting > Advanced hunting > Create detection rule. |

**What to know for the exam**

- Custom detections use advanced hunting queries across Defender XDR data.
- The query must return required columns for impacted entities, typically Timestamp and entity identifiers such as DeviceId, AccountObjectId, or ReportId depending on rule type.
- Rules can run at configured frequencies including near-real-time for supported tables/scenarios.
- Detection rules generate alerts and can optionally trigger response actions on devices or files.
- Keep queries specific to avoid excessive alert volume.

**Key distinctions**

- Advanced hunting query = manual/proactive query. Custom detection = scheduled operational detection built from that query.
- Defender XDR custom detections are not Sentinel analytics rules, though both use KQL.

**Likely exam traps**

- Do not choose a Sentinel scheduled analytics rule when the requirement says Advanced Hunting in Defender XDR.
- If the query does not return required entity columns, it cannot drive proper alerts/actions.

| SC-200 | Detail |
| --- | --- |
| Cram version | Advanced hunting + required entity columns + schedule = Defender XDR custom detection. |

**Manage custom detection rules in Microsoft Defender XDR**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how to maintain Defender XDR custom detections: enable/disable, edit, tune, scope, monitor results, and control response actions. |
| Portal / path | Microsoft Defender portal > Hunting > Custom detection rules. |

**What to know for the exam**

- Review detection status, last run, failures, and alert volume.
- Edit KQL, schedule/frequency, severity, category, MITRE techniques, impacted entities, and response actions.
- Disable or tune noisy rules.
- Use clear naming, descriptions, recommended actions, and MITRE mapping for analyst usability.
- Control scope so rules only query or act on intended devices/entities.

**Key distinctions**

- Managing a detection is operational lifecycle work; creating the original KQL is only the first step.
- Alert tuning handles noise after alerts are generated; editing KQL prevents bad matches at source.

**Likely exam traps**

- Do not leave broad proof-of-concept hunting queries running as detections.
- Do not set automatic response actions on low-confidence detections.

| SC-200 | Detail |
| --- | --- |
| Cram version | Manage custom detections by monitoring failures/noise, tuning KQL, setting scope, mapping MITRE, and controlling actions. |

**Configure and manage analytics rules in Microsoft Sentinel SIEM, including scheduled, near-real time (NRT), threat intelligence, and machine learning**

| SC-200 | Detail |
| --- | --- |
| What this means | Know the main Sentinel analytics rule types and when to use each to generate alerts/incidents from ingested data. |
| Portal / path | Microsoft Sentinel > Analytics > Create rule. |

**What to know for the exam**

- Scheduled rules run KQL on a schedule with a lookback period.
- NRT rules run close to ingestion time but have constraints on query complexity and supported scenarios.
- Threat intelligence rules match ingested threat indicators against event data.
- Microsoft security or machine learning rules provide built-in detections from Microsoft content.
- Rules define tactics/techniques, severity, entity mapping, alert grouping, incident creation, and automated response options.

**Key distinctions**

- Scheduled/NRT analytics rules are Sentinel detections. Defender XDR custom detections are separate, although both use KQL.
- Analytics rules create alerts/incidents; automation rules act on them.

**Likely exam traps**

- Do not pick workbook when asked to create a detection.
- Use NRT only where low latency is required and query constraints can be met.
- Entity mapping is important for incident graph and investigation quality.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel analytics rules turn log patterns into alerts/incidents. Scheduled = flexible. NRT = faster/limited. TI = indicator matching. ML = built-in intelligence. |

**Analyze attack vector coverage by using the MITRE ATT&CK matrix**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how to assess detection coverage across tactics and techniques using MITRE ATT&CK in Defender XDR and Sentinel. |
| Portal / path | Microsoft Sentinel > MITRE ATT&CK / Analytics coverage views; Defender portal incident/alert categories and advanced hunting/detection mapping also use MITRE. |

**What to know for the exam**

- MITRE tactics describe attacker goals such as Initial Access, Execution, Persistence, Privilege Escalation, Defense Evasion, Credential Access, Discovery, Lateral Movement, Collection, Command and Control, Exfiltration, and Impact.
- Analytics rules and custom detections can be mapped to MITRE techniques.
- Coverage views help find detection gaps and over-concentration.
- Coverage does not prove effectiveness; rule quality and data availability are still required.
- Use MITRE mapping to communicate SOC coverage and prioritise new detections.

**Key distinctions**

- MITRE coverage = detection mapping. It is not the same as vulnerability exposure or Secure Score.
- A mapped rule is only useful if required data is ingested and the logic is enabled.

**Likely exam traps**

- Do not assume 100% matrix coverage means secure. ATT&CK mapping can be superficial.
- If no data source exists, enabling a rule will not produce useful detections.

| SC-200 | Detail |
| --- | --- |
| Cram version | MITRE ATT&CK coverage shows which attacker behaviours your detections address; data and rule quality still matter. |

**Configure anomalies in Microsoft Sentinel**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Sentinel anomaly rules use machine learning/statistical baselines to identify abnormal activity. |
| Portal / path | Microsoft Sentinel > Analytics > Anomalies, or built-in anomaly rule configuration depending on portal version. |

**What to know for the exam**

- Anomalies detect deviations from normal behaviour, often without a fixed static threshold.
- They can supplement scheduled analytics rules and hunting.
- Anomaly rules may generate anomalies that can be used in analytics, incidents, or investigation context.
- Tune anomaly sensitivity and suppression carefully to reduce noise.
- Useful for behaviours such as unusual sign-in, network, process, or data access patterns depending on available content.

**Key distinctions**

- Anomaly = behaviour deviation. Analytics rule = configured detection logic. UEBA = user/entity behaviour analytics context.
- Not every anomaly should become a high-severity incident.

**Likely exam traps**

- Do not use anomaly detections for deterministic IOC matching; use threat intelligence rules or exact KQL logic.
- Do not treat anomalies as proof of compromise without investigation.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel anomalies = ML/statistical unusual behaviour signals; tune sensitivity and investigate context. |

# Respond to security incidents (35-40%)

## Respond to alerts and incidents in Microsoft Defender XDR

**Investigate and remediate threats by using Microsoft Defender for Office 365, including automatic attack disruption**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how MDO investigations handle phishing, malware, malicious URLs, user submissions, Explorer, AIR, and email remediation. |
| Portal / path | Microsoft Defender portal > Email & collaboration > Explorer / Review > Submissions / Incidents & alerts > Incidents. |

**What to know for the exam**

- Use Explorer/Real-time detections to investigate email campaigns, senders, recipients, URLs, attachments, delivery action, and post-delivery events.
- Safe Links protects at time-of-click; Safe Attachments detonates unknown attachments.
- AIR can soft-delete email, block URLs, turn off external forwarding, and turn off delegation depending on scenario.
- Submissions portal is used for admin/user reported emails, URLs, and attachments for Microsoft analysis.
- Automatic attack disruption may act when BEC/phishing-related compromise is correlated across Defender XDR.

**Key distinctions**

- Safe Links = URL protection. Safe Attachments = attachment detonation. Anti-phishing = impersonation/spoofing protection. Explorer = investigation.
- Email remediation actions appear in Action Center.

**Likely exam traps**

- Do not use Content Search as the first choice for security triage when Defender for Office 365 Explorer/AIR is available for email threat investigation.
- Do not confuse user submission analysis with releasing quarantine.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDO response = Explorer, submissions, AIR, URL/email remediation, and Safe Links/Safe Attachments context. |

**Investigate and remediate threats or compromised entities identified by Microsoft Purview**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Purview contributes data sensitivity, audit, DLP, insider risk, eDiscovery, and content investigation context to security operations. |
| Portal / path | Microsoft Purview portal for Audit, Content Search, DLP, Insider Risk, eDiscovery, and Information Protection. Defender XDR may show sensitive data context in incidents when Purview Information Protection is enabled. |

**What to know for the exam**

- Purview Information Protection labels can surface data sensitivity context in Defender incidents.
- Purview Audit can investigate Microsoft 365 user/admin activities.
- Content Search/eDiscovery can locate content across Exchange, SharePoint, OneDrive, and Teams for investigation or legal hold workflows.
- DLP alerts/incidents may indicate attempted exfiltration or policy violations.
- Remediation can include label changes, DLP policy actions, access review, deletion/preservation, or escalation to compliance/legal.

**Key distinctions**

- Purview is compliance/data security. Defender XDR is threat detection/response. They overlap during data exfiltration and compromised entity investigations.
- Content Search finds content; Audit shows activity; DLP shows policy violations.

**Likely exam traps**

- Do not use Defender for Endpoint device timeline to answer a question asking specifically about Microsoft 365 content search or audit activity.
- Do not ignore sensitivity labels when prioritising incidents involving data exfiltration.

| SC-200 | Detail |
| --- | --- |
| Cram version | Purview adds data, audit, DLP, and content context to incidents; use Audit for activity and Content Search for content location. |

**Investigate and remediate alerts and incidents identified by Microsoft Defender for Cloud workload protections**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Defender for Cloud workload protection alerts are investigated and remediated for servers, storage, containers, databases, app services, and other cloud workloads. |
| Portal / path | Microsoft Defender portal / Azure portal > Microsoft Defender for Cloud > Security alerts / Recommendations / Workload protections; Sentinel may ingest alerts/incidents through connectors. |

**What to know for the exam**

- Defender for Cloud provides CSPM recommendations and CWPP alerts for cloud/hybrid workloads.
- Workload protection plans cover resources such as Servers, Storage, SQL, Containers, App Service, Key Vault, and others depending on enabled plans.
- Investigations often require reviewing affected resource, alert evidence, MITRE tactic, recommendation, vulnerability, and activity logs.
- Remediation may include patching, hardening configuration, disabling public access, rotating secrets, isolating workload, or enabling missing protections.
- Sentinel can correlate Defender for Cloud alerts with other SIEM data.

**Key distinctions**

- Defender for Cloud = cloud posture and workload protection. Defender for Endpoint = endpoint EDR. Defender XDR incident page can include cloud alerts, but cloud configuration often lives in Defender for Cloud/Azure.
- Security recommendation = posture gap. Security alert = detected suspicious activity.

**Likely exam traps**

- Do not treat posture recommendations as incidents unless there is detected malicious activity.
- Do not assume App Service WAF and Defender for App Service protect the same layer; WAF filters HTTP traffic, Defender detects workload/platform threats.

| SC-200 | Detail |
| --- | --- |
| Cram version | Defender for Cloud response = investigate workload alert/resource/evidence, then remediate cloud configuration, vulnerability, or compromised workload. |

**Investigate and remediate security risks identified by Microsoft Defender for Cloud Apps**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how MDCA handles SaaS app discovery, OAuth app governance, cloud app alerts, session controls, and risky cloud activity investigations. |
| Portal / path | Microsoft Defender portal > Cloud apps, or Defender for Cloud Apps experiences integrated into Defender XDR. |

**What to know for the exam**

- Cloud Discovery identifies shadow IT through Defender for Endpoint integration, firewall/proxy logs, or network appliances.
- Policies can detect risky activities such as impossible travel, mass downloads, suspicious inbox rules, OAuth app abuse, and anomalous SaaS usage.
- Conditional Access App Control can apply session controls such as block download, require monitoring, or protect data in real time.
- App governance focuses on OAuth apps and permissions risk.
- Remediation may include suspending user, revoking OAuth app consent, blocking app, applying session policy, or tuning policies.

**Key distinctions**

- MDCA = SaaS/CASB security. Entra Conditional Access = access decision engine. Conditional Access App Control = reverse-proxy session control provided by MDCA.
- Cloud app risk is not the same as Azure workload risk.

**Likely exam traps**

- Do not choose Defender for Cloud when the scenario is SaaS shadow IT or OAuth app risk; choose Defender for Cloud Apps/app governance.
- Do not confuse app sanctioning with blocking user sign-in through Conditional Access.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDCA response = investigate SaaS activity, OAuth apps, shadow IT, and session controls; remediate by blocking apps, revoking OAuth, or controlling sessions. |

**Investigate and remediate compromised identities that are identified by Microsoft Entra ID**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Entra ID Protection identifies risky users, risky sign-ins, and risk detections and how analysts remediate identity risk. |
| Portal / path | Microsoft Entra admin center > Protection > Identity Protection > Risky users / Risky sign-ins / Risk detections. Defender portal may surface related identity alerts/incidents. |

**What to know for the exam**

- Risky users show accounts with calculated compromise probability.
- Risky sign-ins show suspicious authentication attempts and Conditional Access results.
- Risk detections include anonymous IP, atypical travel, leaked credentials, password spray, unfamiliar sign-in properties, threat actor IP, and token anomalies.
- Remediation includes require password change, reset password, confirm compromised, dismiss risk, block sign-in, or allow self-remediation through MFA/SSPR.
- User risk policy and sign-in risk policy automate responses when thresholds are met.

**Key distinctions**

- User risk = account may be compromised. Sign-in risk = this authentication attempt may be suspicious.
- Entra ID Protection protects cloud identities; Defender for Identity protects on-prem AD/hybrid identity signals.

**Likely exam traps**

- Do not dismiss user risk simply because the user is blocked; risk should be investigated/remediated.
- Do not choose sign-in risk policy when the scenario asks to force password change for a compromised account; user risk policy is usually relevant.

| SC-200 | Detail |
| --- | --- |
| Cram version | Entra ID Protection response = investigate risky users/sign-ins/detections, then reset/change password, require MFA, confirm compromised/safe, or dismiss risk. |

**Investigate and remediate security alerts from Microsoft Defender for Identity**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how MDI detects on-prem AD and hybrid identity attacks such as reconnaissance, credential compromise, lateral movement, and domain dominance. |
| Portal / path | Microsoft Defender portal > Incidents & alerts > Incidents / Alerts, and Settings > Identities for sensor health/configuration. |

**What to know for the exam**

- MDI sensors are installed on domain controllers, AD FS, AD CS, and Entra Connect servers depending on coverage requirements.
- Alerts include reconnaissance, brute force/password spray, suspected identity theft, pass-the-ticket, overpass-the-hash, remote code execution on DC, DCShadow, and other domain dominance behaviours.
- Investigation uses alert timeline, evidence, involved users/computers, lateral movement paths, and related Defender XDR incident graph.
- Remediation may include disabling/resetting accounts, revoking sessions, isolating compromised endpoints, removing persistence, hardening AD, and addressing lateral movement paths.
- Sensor health is critical; no sensor visibility means missing on-prem identity signals.

**Key distinctions**

- MDI = on-prem AD/hybrid identity attack detection. Entra ID Protection = cloud identity risk. MDE = endpoint telemetry.
- Lateral movement path analysis indicates exposure paths, not necessarily confirmed movement.

**Likely exam traps**

- Do not install MDI sensor on every workstation; sensors belong on identity infrastructure such as DCs/AD FS/AD CS/Entra Connect.
- Do not treat a single MDI alert in isolation when Defender XDR has correlated it into a broader incident.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDI response = investigate AD attack alerts, users/computers, lateral movement, and domain dominance indicators; remediate identity and endpoint compromise. |

**Investigate and remediate alerts and incidents identified by Microsoft Sentinel**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Sentinel incidents are triaged, investigated, assigned, enriched, remediated, and closed. |
| Portal / path | Microsoft Sentinel > Incidents, Investigation graph, Entity pages, Automation, Hunting, Logs. |

**What to know for the exam**

- Sentinel incidents are created by analytics rules, Fusion, Microsoft security incidents, or other integrations.
- Incident management includes assign owner, set severity/status, add tags/comments, classify, and close with reason.
- Investigation graph shows related entities and alerts.
- Entities link to context such as account, host, IP, URL, file hash, cloud resource, or process.
- Remediation often uses playbooks, Defender actions, Azure actions, identity actions, firewall/block lists, or ticketing workflows.

**Key distinctions**

- Sentinel is the SIEM/SOAR layer. Defender XDR is the Microsoft XDR layer. Integrated incidents can synchronise between portals, but the investigation source and correlation engine matter.
- Playbooks automate response; incident management documents the case.

**Likely exam traps**

- Do not close incidents without classification/determination in exam scenarios that ask for case management.
- Do not build a playbook when simple assignment/tag/status changes can be handled by automation rules.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel response = triage incident, review alerts/entities/graph/logs, run playbooks/actions, document and close with classification. |

**Investigate incidents by using agentic AI, including embedded Copilot for Security**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how embedded Security Copilot and agents assist investigations, summarise incidents, explain evidence, triage phishing, and produce threat intelligence briefings. |
| Portal / path | Microsoft Defender portal Copilot side panel / embedded Copilot experiences; Security Copilot portal; agent pages such as Phishing Triage Agent, Threat Intelligence Briefing Agent, and Identity Risk Management Agent where available. |

**What to know for the exam**

- Copilot can summarise incidents, explain alerts, generate investigation steps, assist KQL, and draft reports.
- Phishing Triage Agent classifies user-reported phishing alerts and provides transparent reasoning.
- Threat Intelligence Briefing Agent generates briefings based on threat activity and vulnerability context.
- Identity Risk Management Agent analyses risky users and suggests remediation.
- Agents require Security Copilot capacity/SCUs, plugins, permissions, and appropriate product prerequisites.

**Key distinctions**

- Copilot assists and accelerates; the analyst remains accountable.
- Agent identity permissions must follow least privilege.
- Embedded Copilot in Defender is different from Sentinel notebooks or KQL jobs.

**Likely exam traps**

- Do not assume AI can take actions without permissions and configuration.
- Do not trust output blindly; review evidence and reasoning before action.

| SC-200 | Detail |
| --- | --- |
| Cram version | Agentic AI = Copilot/agents summarise, triage, reason and recommend; analysts validate and act. |

**Investigate complex attacks, such as multi-stage, multi-domain, and lateral movement**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how to use Defender XDR and Sentinel to reconstruct attack chains across email, endpoint, identity, SaaS, cloud workloads, and data. |
| Portal / path | Microsoft Defender portal > Incidents > incident page, graph, timeline, evidence, entities; Microsoft Sentinel > Incidents > Investigation graph / Logs / Hunting. |

**What to know for the exam**

- Complex attacks often combine phishing, endpoint execution, credential theft, privilege escalation, lateral movement, cloud app access, and data exfiltration.
- Use incident timeline to understand sequence and root cause.
- Use evidence/entities to pivot across users, devices, mailboxes, files, IPs, URLs, apps, and cloud resources.
- Use device timeline, email Explorer, identity alerts, cloud app activity, and Sentinel logs for broader context.
- Containment should target current attacker control points and likely propagation paths.

**Key distinctions**

- Multi-stage = sequence across kill chain. Multi-domain = multiple security workloads. Lateral movement = moving between devices/accounts/resources.
- Blast radius/attack path visualisations show potential and actual spread context.

**Likely exam traps**

- Do not remediate only the initial phishing email if endpoint and identity compromise followed.
- Do not assume an incident with many alerts is worse than one high-confidence domain dominance alert; severity and business impact matter.

| SC-200 | Detail |
| --- | --- |
| Cram version | Complex attack investigation = timeline + entities + graph + workload pivots + containment of users/devices/paths. |

**Manage security incidents by using case management**

| SC-200 | Detail |
| --- | --- |
| What this means | Know the operational case management tasks: ownership, status, classification, determination, comments, tags, evidence handling, and closure. |
| Portal / path | Microsoft Defender portal > Incidents & alerts > Incidents. Microsoft Sentinel > Incidents. Ticketing integrations may exist through playbooks/connectors. |

**What to know for the exam**

- Assign incidents to an analyst or queue.
- Update status such as Active/In progress/Resolved depending on portal.
- Set classification such as True positive, False positive, Informational/expected activity, and determination where available.
- Add comments, tags, and history notes to record decisions and actions.
- Escalate to incident response, legal, communications, or business owners when impact requires it.

**Key distinctions**

- Case management is about managing the investigation record, not detecting threats.
- Classification improves detection quality and SOC reporting.

**Likely exam traps**

- Do not close as false positive when the activity is real but authorised; use expected/benign activity where applicable.
- Do not confuse assigning an incident with remediating the underlying threat.

| SC-200 | Detail |
| --- | --- |
| Cram version | Case management = owner, status, severity, tags, comments, classification/determination, evidence, escalation, closure. |

## Respond to alerts and incidents in Microsoft Defender for Endpoint

**Investigate device timelines**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how the MDE device timeline shows chronological endpoint activity for process, file, network, registry, logon, and security events. |
| Portal / path | Microsoft Defender portal > Assets > Devices > select device > Timeline. |

**What to know for the exam**

- Timeline is used to reconstruct what happened on a device before, during, and after an alert.
- Events include process creation, file changes, network connections, registry modifications, logons, image loads, and AV/security events depending on telemetry.
- Use filters for event type, time range, entity, file name, process, IP, URL, or action type.
- Pivot from timeline events to files, processes, users, alerts, and advanced hunting.
- Timeline helps validate whether malware executed, persistence was created, or lateral movement occurred.

**Key distinctions**

- Device timeline = chronological endpoint evidence. Advanced hunting = query across many devices/tables.
- Timeline is device-centric; incident graph is cross-entity/cross-domain.

**Likely exam traps**

- Do not rely only on alert title; timeline may show pre-alert and post-alert activity.
- Do not confuse device timeline with Sentinel investigation graph.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDE device timeline = endpoint chronology for process/file/network/registry/logon events. Use it to reconstruct compromise. |

**Perform actions on the device, including live response and collecting investigation packages**

| SC-200 | Detail |
| --- | --- |
| What this means | Know the main MDE response actions available against devices and when to use Live Response or investigation package collection. |
| Portal / path | Microsoft Defender portal > Assets > Devices > select device > Response actions. Live Response requires permissions and supported OS/onboarding. |

**What to know for the exam**

- Common actions include isolate device, restrict app execution, run antivirus scan, collect investigation package, initiate automated investigation, offboard device, and consult device action history.
- Collect investigation package gathers diagnostic and forensic artefacts in a ZIP package.
- Live Response provides an interactive remote shell-like response session for approved commands such as collect file, run script, list processes, or remediate artefacts.
- Actions require appropriate RBAC permissions and may require device to be online.
- Device isolation allows Defender service connectivity while blocking most other network communications.

**Key distinctions**

- Collect investigation package = gather evidence. Live Response = interactive investigation/remediation. Isolate device = containment.
- Restrict app execution differs from full isolation.

**Likely exam traps**

- Do not choose Live Response if the task only asks to gather standard investigation artefacts; collect investigation package may be correct.
- Do not isolate a business-critical server without considering impact unless the scenario demands containment.

| SC-200 | Detail |
| --- | --- |
| Cram version | MDE device actions = isolate, restrict, scan, collect package, start AIR, Live Response. Match action to containment/evidence/remediation need. |

**Perform evidence and entity investigation**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Defender XDR/MDE evidence pages and entities support investigation of files, processes, users, devices, IPs, URLs, and mailboxes. |
| Portal / path | Microsoft Defender portal > Incidents > Evidence and response / Entities, or individual entity pages such as Device page, File page, User page, IP/URL page. |

**What to know for the exam**

- Evidence has verdicts such as malicious, suspicious, or clean/no threats found.
- Entity pages centralise alerts, observed activity, prevalence, timeline, incidents, exposure, and available actions.
- File investigation can include hash, prevalence, signer/certificate, AV detection, and where seen.
- User investigation can include alerts, sign-ins, risky status, cloud app activity, and related devices.
- Evidence and response view shows remediation state and available actions.

**Key distinctions**

- Evidence = artefacts involved in an incident. Entity = object being investigated. Alert = detection. Incident = correlated case.
- Prevalence helps estimate whether a file/process is common or rare in the organisation/global telemetry.

**Likely exam traps**

- Do not remediate an entity without checking whether it is business-critical or known legitimate.
- Do not ignore suspicious entities with no current alert if they sit in the incident graph.

| SC-200 | Detail |
| --- | --- |
| Cram version | Evidence/entity investigation = inspect artefacts, verdicts, prevalence, relationships and remediation state. |

**Investigate and remediate incidents identified by automatic attack disruption**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how to review Defender XDR incidents where automatic attack disruption has already taken containment actions. |
| Portal / path | Microsoft Defender portal > Incidents > select incident > Summary / Evidence and response / Action center / Attack disruption details where shown. |

**What to know for the exam**

- Review what disruption actions were taken, why, and on which entities.
- Validate whether user/device containment succeeded and whether further remediation is needed.
- Check Action Center history for action source and status.
- Continue root-cause investigation; disruption is containment, not full eradication.
- Undo or modify actions only after confirming the entity is safe and business impact justifies it.

**Key distinctions**

- Attack disruption = automatic containment. Incident remediation = full investigation, eradication, recovery, and closure.
- Action Center records actions; incident timeline explains attack sequence.

**Likely exam traps**

- Do not assume attack disruption closes the incident automatically.
- Do not reverse containment before confirming credentials, devices, persistence, and related entities are clean.

| SC-200 | Detail |
| --- | --- |
| Cram version | For attack disruption incidents: review actions, validate containment, continue root cause, remediate fully, then close. |

## Investigate Microsoft 365 activities to identify threats

**Investigate threats by using Audit from Microsoft Purview**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Microsoft Purview Audit is used to search Microsoft 365 user and admin activity for investigation. |
| Portal / path | Microsoft Purview portal > Audit. |

**What to know for the exam**

- Audit records activities across Exchange, SharePoint, OneDrive, Teams, Entra ID, Power Platform and other Microsoft 365 services depending on licensing and workload.
- Search by user, activity, date/time, file/site/mailbox, IP address, workload, or record type.
- Use Audit to investigate actions such as file access/download, mailbox rule creation, sharing changes, admin operations, Teams activity, and eDiscovery/compliance actions.
- Audit evidence can support incident timeline and scope analysis.
- Export results for deeper analysis where needed.

**Key distinctions**

- Audit = activity log search. Content Search = find content. Defender XDR = threat incident investigation.
- Audit tells what happened; it may not decide whether it was malicious.

**Likely exam traps**

- Do not use Content Search when the question asks who performed an action; use Audit.
- Do not assume audit retention is unlimited; licensing and configuration matter.

| SC-200 | Detail |
| --- | --- |
| Cram version | Purview Audit = search Microsoft 365 user/admin activities to determine who did what, when, where, and from which workload. |

**Investigate threats by using Content Search in Microsoft Purview**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Content Search locates content across Microsoft 365 locations for investigation, legal/compliance, or remediation scoping. |
| Portal / path | Microsoft Purview portal > Solutions > Content Search / eDiscovery. |

**What to know for the exam**

- Content Search can search mailboxes, SharePoint sites, OneDrive accounts, and Microsoft Teams-related content.
- Use keywords, KQL conditions, sender/recipient, dates, subject, file types, and locations.
- Useful for finding malicious emails, sensitive data exposure, or compromised content across Microsoft 365.
- Results can be previewed/exported depending on permissions.
- Security teams may use it with eDiscovery/legal processes; use least privilege and proper approvals.

**Key distinctions**

- Content Search = find content. Audit = activity log. Explorer = security-focused email investigation in Defender for Office 365.
- Content Search is powerful but not always the fastest SOC tool for phishing when MDO Explorer/AIR is available.

**Likely exam traps**

- Do not use Content Search to see Conditional Access evaluation; use sign-in logs.
- Do not confuse searching for content with remediating it.

| SC-200 | Detail |
| --- | --- |
| Cram version | Content Search = locate Microsoft 365 content across mailboxes/sites/OneDrive/Teams using search criteria. |

**Investigate threats by using Microsoft Graph activity logs**

| SC-200 | Detail |
| --- | --- |
| What this means | Know that Microsoft Graph activity logs provide visibility into Microsoft Graph API requests, useful for investigating app abuse, data access, and OAuth/service principal activity. |
| Portal / path | Microsoft Entra admin center / Azure Monitor diagnostic settings to send Microsoft Graph activity logs to Log Analytics/Sentinel where available; query in Sentinel/Log Analytics. |

**What to know for the exam**

- Graph activity logs help identify API calls made against Microsoft Graph, including app/service principal access patterns.
- Useful for investigating OAuth app compromise, excessive data reads, suspicious app permissions, and unusual API activity.
- Logs generally need diagnostic settings or supported export to Log Analytics/Sentinel.
- Investigate app ID, service principal, user, resource, operation, IP, and result.
- Correlate with Entra sign-ins, audit logs, app consent events, Defender for Cloud Apps app governance, and Sentinel incidents.

**Key distinctions**

- Graph activity logs = API activity. Entra sign-in logs = authentication events. Audit logs = directory/admin changes.
- Service principal activity can be non-interactive and may not look like a user sign-in.

**Likely exam traps**

- Do not assume a compromised OAuth app will trigger only user risk; app/API logs may be needed.
- Do not confuse Microsoft Graph Security API with Graph activity logs; one is an API surface, the other is telemetry about Graph calls.

| SC-200 | Detail |
| --- | --- |
| Cram version | Graph activity logs = visibility into Microsoft Graph API calls for app/user/service principal investigation. |

# Perform threat hunting (20-25%)

## Detect threats by using Microsoft Defender XDR

**Identify the appropriate table to use in a KQL query**

| SC-200 | Detail |
| --- | --- |
| What this means | Know which Defender XDR advanced hunting table contains the data needed for a hunting question. |
| Portal / path | Microsoft Defender portal > Hunting > Advanced hunting > Schema reference. |

**What to know for the exam**

- DeviceProcessEvents = process creation and command-line activity.
- DeviceFileEvents = file creation/modification/deletion events.
- DeviceNetworkEvents = endpoint network connections.
- DeviceRegistryEvents = registry changes.
- DeviceLogonEvents = device sign-ins/logons.
- EmailEvents, EmailUrlInfo, EmailAttachmentInfo, EmailPostDeliveryEvents = email delivery, URLs, attachments, and post-delivery actions.
- IdentityLogonEvents, IdentityDirectoryEvents, IdentityQueryEvents, IdentityInfo = identity/authentication and directory activity.
- CloudAppEvents = SaaS/cloud app activities.
- AlertInfo and AlertEvidence = alerts and related evidence.

**Key distinctions**

- Pick the table by event type first, then join/enrich if needed.
- Entity tables such as DeviceInfo/IdentityInfo describe current or periodic entity state; event tables describe activities.

**Likely exam traps**

- Do not query DeviceProcessEvents for email URL clicks; use email/cloud app/browser-related data depending on scenario.
- Do not forget advanced hunting timestamps are UTC.

| SC-200 | Detail |
| --- | --- |
| Cram version | Choose KQL table by data: process/file/network/registry/logon/email/identity/cloud app/alert evidence. |

**Identify threats by using Kusto Query Language (KQL)**

| SC-200 | Detail |
| --- | --- |
| What this means | Know the KQL operators and patterns used to find suspicious activity in Defender XDR and Sentinel. |
| Portal / path | Defender portal > Advanced hunting, or Sentinel > Logs / Hunting. |

**What to know for the exam**

- Core operators: where, project, extend, summarize, join, union, order by, top, distinct, parse, mv-expand.
- Use time filters such as Timestamp > ago(24h) or TimeGenerated > ago(24h).
- Use has/contains/in/startswith/endswith and case-insensitive operators carefully.
- Summarize helps identify spikes, rare values, multiple failures, or suspicious counts.
- Join tables to connect entities, such as alerts to evidence or process events to device info.

**Key distinctions**

- Defender advanced hunting often uses Timestamp; Sentinel Log Analytics tables often use TimeGenerated.
- KQL is query language, not a response mechanism by itself.

**Likely exam traps**

- Do not forget to limit time range and project useful columns.
- Do not use contains when has/in would be more precise and efficient for tokenized matches.

| SC-200 | Detail |
| --- | --- |
| Cram version | KQL hunting = filter time, select table, where suspicious condition, project evidence, summarize patterns, join context. |

**Create Advanced Hunting queries**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how to build practical Defender XDR advanced hunting queries that can be run manually or converted to custom detections. |
| Portal / path | Microsoft Defender portal > Investigation & response > Hunting > Advanced hunting. |

**What to know for the exam**

- Start with a hypothesis such as credential theft, PowerShell abuse, suspicious inbox rules, rare process execution, or malicious URL clicks.
- Use schema reference and sample queries to identify fields and action types.
- Build incrementally: table -> time filter -> event filter -> projection -> enrichment -> summarisation.
- Validate results before creating a custom detection.
- Save useful queries for reuse and share with the SOC.

**Key distinctions**

- Advanced hunting queries can inspect up to available retention in Defender XDR; Sentinel may retain logs longer.
- Custom detections require query outputs suitable for alerting and entity mapping.

**Likely exam traps**

- Do not operationalize a query that returns normal day-to-day admin activity without exclusions.
- Do not ignore false positive handling and recommended actions when creating detections.

| SC-200 | Detail |
| --- | --- |
| Cram version | Advanced hunting query workflow: hypothesis -> table -> time filter -> suspicious filter -> project evidence -> validate -> save/detect. |

**Interpret threat analytics in Microsoft Defender XDR**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Threat Analytics reports provide Microsoft intelligence about active threats, exposure, indicators, vulnerabilities, and recommended actions. |
| Portal / path | Microsoft Defender portal > Threat intelligence > Threat analytics. |

**What to know for the exam**

- Threat Analytics reports describe campaigns, malware, threat actors, techniques, affected products, IOCs, and mitigations.
- Reports may show organisational exposure such as vulnerable devices, alerts, incidents, or observed indicators.
- Use reports to prioritise patching, hunting, detection, and mitigation actions.
- Threat Intelligence Briefing Agent can generate summarised briefings when Security Copilot prerequisites are met.
- Threat Analytics is useful for both tactical investigation and management reporting.

**Key distinctions**

- Threat Analytics = intelligence reporting. Advanced hunting = query your data. Threat indicators = IOCs ingested or used for matching.
- A threat report is not automatically evidence of compromise in your tenant; check exposure and observed activity.

**Likely exam traps**

- Do not treat global threat news as tenant compromise without local evidence.
- Do not ignore recommended actions and exposed assets in the report.

| SC-200 | Detail |
| --- | --- |
| Cram version | Threat Analytics = Microsoft threat intelligence reports plus tenant exposure context and recommended actions. |

**Create hunting graphs, including blast radius**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how graph-based hunting and blast radius analysis visualise relationships and attack paths across entities. |
| Portal / path | Microsoft Defender portal > Advanced hunting > Hunting graph; incident graph > View blast radius where available. Requires relevant graph/data lake/exposure management prerequisites. |

**What to know for the exam**

- Hunting graph represents entities as nodes and relationships as edges.
- Use predefined scenarios to explore paths between entities, access to sensitive data, key vault access, Kubernetes reachability, SQL data paths, or Azure DevOps repository access.
- Blast radius analysis extends incident graph to show current impact and potential future propagation paths to critical targets.
- Use graph findings to prioritise containment, segmentation, least privilege, and remediation.
- Graph paths are possible paths based on known relationships, not proof that movement occurred.

**Key distinctions**

- Hunting graph = proactive graph exploration. Blast radius = incident-centric impact/propagation analysis.
- Graph analysis complements KQL; it does not replace event evidence.

**Likely exam traps**

- Do not assume every graph path was used by an attacker.
- Do not ignore RBAC: graph visibility is scoped to user permissions.

| SC-200 | Detail |
| --- | --- |
| Cram version | Graph hunting = nodes/edges/paths. Blast radius = current and potential incident impact paths to critical assets. |

**Analyze relationships between entities by using Sentinel Graph**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Sentinel Graph provides relationship-based context across entities, helping analysts identify paths, dependencies, and high-risk relationships. |
| Portal / path | Microsoft Sentinel graph / data lake graph experiences integrated with Defender portal hunting graph and blast radius features where available. |

**What to know for the exam**

- Sentinel Graph stores and renders relationships between entities such as identities, devices, cloud resources, repositories, storage, and critical assets.
- Use it to understand access paths, lateral movement opportunities, and relationships between attack evidence.
- Entity relationships can include permissions, membership, authentication capability, network routes, ownership, or access to data stores.
- Use graph context to decide where containment or least privilege changes have highest impact.
- It is especially useful when tabular joins become too complex.

**Key distinctions**

- Graph relationship analysis = visual/path-based reasoning. KQL = tabular evidence query. Both are complementary.
- Potential relationship does not equal confirmed malicious activity.

**Likely exam traps**

- Do not use graph alone as final proof of compromise; validate with events.
- Do not expect graph data without prerequisites such as Sentinel data lake/graph onboarding where required.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel Graph = relationship analysis across entities to expose paths, dependencies, and high-leverage remediation points. |

## Detect threats by using the Microsoft Sentinel platform

**Create and monitor hunting queries**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how Sentinel hunting queries are used for proactive threat hunting over SIEM data. |
| Portal / path | Microsoft Sentinel > Hunting. |

**What to know for the exam**

- Hunting queries are saved KQL queries designed to find suspicious patterns, not necessarily generate incidents automatically.
- Built-in hunting queries are provided by content solutions and can be customised.
- Run queries manually, review results, bookmark interesting findings, and promote useful logic to analytics rules where appropriate.
- Hunting queries should be mapped to tactics/techniques and documented with clear intent.
- Monitor query results over time to identify trends and candidates for operationalisation.

**Key distinctions**

- Hunting query = proactive/manual investigation. Analytics rule = scheduled detection and incident generation. Bookmark = preserve hunting evidence.
- Not every hunting query should become an alert.

**Likely exam traps**

- Do not confuse hunting bookmarks with incident comments.
- Do not create high-volume analytics rules from broad hunting queries without tuning.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel hunting queries = saved proactive KQL. Run, review, bookmark, refine, and promote to analytics only when mature. |

**Create and manage KQL jobs in Data lake**

| SC-200 | Detail |
| --- | --- |
| What this means | Know the concept of running KQL jobs over Sentinel data lake data for large-scale or longer-retention analysis. |
| Portal / path | Microsoft Sentinel data lake / Defender portal data lake experiences, depending on tenant capability. |

**What to know for the exam**

- KQL jobs are useful for querying large data volumes or lower-cost retained data outside normal interactive analytics paths.
- They can support investigations over extended retention periods.
- Jobs may be asynchronous, with results stored for later review.
- Use them when immediate analytics-tier query performance is not required or when querying data lake-scale data.
- Permissions and data lake onboarding are prerequisites.

**Key distinctions**

- Interactive Logs query = immediate investigation against active tables. KQL job = managed/asynchronous analysis over data lake scale or retained data.
- Data lake is not the same as standard Log Analytics analytics tier.

**Likely exam traps**

- Do not choose KQL jobs for low-latency alerting; use Sentinel analytics rules or NRT where appropriate.
- Do not assume all Sentinel tenants have data lake capabilities enabled.

| SC-200 | Detail |
| --- | --- |
| Cram version | KQL jobs in data lake = asynchronous/large-scale/long-retention analysis, not real-time alerting. |

**Create and manage Summary rule tables for querying**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how summary rules precompute or aggregate data into summary tables to improve query performance and reduce repeated expensive computation. |
| Portal / path | Microsoft Sentinel / Log Analytics data management experiences for summary rules/tables where available. |

**What to know for the exam**

- Summary rules run KQL on source data and write summarised results into a summary table.
- Use cases include high-volume logs, long lookback trend analysis, dashboards, cost-aware hunting, and repeated aggregations.
- Summary tables can make workbooks and hunting queries faster and cheaper.
- Choose aggregation granularity carefully so the summary preserves investigative value.
- Manage rule schedule, lookback, destination table, and retention.

**Key distinctions**

- Summary table = precomputed aggregated data. Raw table = original detailed events.
- Summary rules support analytics/hunting efficiency; they are not the same as analytics rules that create incidents.

**Likely exam traps**

- Do not summarise away fields needed for investigation.
- Do not use summary tables when raw, per-event fidelity is required for evidence.

| SC-200 | Detail |
| --- | --- |
| Cram version | Summary rules precompute useful aggregations into summary tables for faster, cheaper queries over high-volume data. |

**Hunt for threats by using Notebooks, including connection to the Sentinel MCP Server**

| SC-200 | Detail |
| --- | --- |
| What this means | Know how notebooks support advanced hunting, data science, enrichment, visualisation, and repeatable investigation workflows in Sentinel. |
| Portal / path | Microsoft Sentinel > Notebooks, typically using Azure Machine Learning / Jupyter environment; connect to Sentinel APIs/data and, where available, Sentinel MCP Server integrations. |

**What to know for the exam**

- Notebooks are useful for complex investigations that need code, visualisation, enrichment, machine learning, or multi-source analysis.
- They can query Log Analytics/Sentinel data, call APIs, enrich indicators, produce charts, and document the investigation.
- Use MSTICPy and other libraries where appropriate for Microsoft security hunting workflows.
- MCP Server connectivity enables AI/tooling workflows to interact with Sentinel data and operations where configured.
- Notebooks are more flexible but require more skill and governance than portal hunting queries.

**Key distinctions**

- Notebook = code-driven investigation. Hunting query = saved KQL in portal. Workbook = dashboard. Playbook = automated response.
- MCP Server is an integration/tooling interface, not a detection rule type.

**Likely exam traps**

- Do not pick notebooks for a simple scheduled detection requirement; use analytics rules.
- Do not run uncontrolled notebooks with excessive permissions or unmanaged secrets.

| SC-200 | Detail |
| --- | --- |
| Cram version | Sentinel notebooks = advanced, code-driven hunting and enrichment; use for complex analysis beyond standard KQL portal hunting. |

## Appendix A - High-yield comparison table

| Thing | Plain English | Use when |
| --- | --- | --- |
| Defender XDR incident | Correlated Microsoft security attack story across Defender workloads | Cross-domain Microsoft attack investigation |
| Sentinel incident | SIEM/SOAR case generated from analytics, Fusion, connectors, or Defender integration | Central SOC case management across Microsoft and non-Microsoft data |
| Advanced hunting | KQL hunting in Defender XDR data | Endpoint/email/identity/cloud app hunting |
| Sentinel Logs | KQL query over Log Analytics/Sentinel tables | SIEM-wide investigation and detection engineering |
| Custom detection | Defender XDR recurring detection from advanced hunting | Create Defender XDR alerts/actions from hunting logic |
| Analytics rule | Sentinel detection rule | Create SIEM alerts/incidents |
| Automation rule | Native Sentinel incident/alert workflow rule | Assign/tag/update/run playbook |
| Playbook | Azure Logic App SOAR workflow | Enrichment, notification, ticketing, containment |
| Workbook | Interactive dashboard/report | Visualisation and reporting |
| Watchlist | Reference dataset for KQL joins/lookups | Asset lists, VIP users, IP ranges |
| ASR rule | Endpoint hardening/prevention control | Block risky behaviours |
| AIR | Automated investigation and remediation | Reduce analyst workload and remediate evidence |

## Appendix B - Last-pass memory lines

- Defender XDR = Microsoft XDR correlation and response across endpoint, identity, email, cloud apps, and cloud workloads.
- Sentinel = SIEM/SOAR platform for Microsoft and non-Microsoft data, analytics, incidents, automation, hunting, workbooks, and notebooks.
- MDE = endpoint telemetry, device timeline, Live Response, AIR, device actions, ASR, indicators, and vulnerability context.
- MDO = email/collaboration protection: Safe Links, Safe Attachments, anti-phishing, Explorer, submissions, email AIR.
- MDI = on-prem AD/hybrid identity attack detection from sensors on identity infrastructure.
- Entra ID Protection = risky users, risky sign-ins, risk detections, user/sign-in risk policies.
- MDCA = SaaS/CASB: cloud app discovery, OAuth app governance, activity policies, session controls.
- Defender for Cloud = cloud posture and workload protection for Azure/hybrid/multicloud resources.
- Purview = audit, data protection, DLP, content search/eDiscovery, sensitivity and compliance context.
- KQL exam tactic: identify table first, filter by time, filter suspicious behaviour, project useful fields, summarize, join context.
