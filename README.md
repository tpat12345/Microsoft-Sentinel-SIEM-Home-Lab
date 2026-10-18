
# Microsoft Sentinel SIEM Home Lab

## Project Overview
Built and configured a cloud-based Security Information and Event Management (SIEM) home lab using Microsoft Sentinel, Microsoft Defender, Azure Monitor, and Log Analytics.

The project demonstrates security monitoring, log collection, KQL detection engineering, alert investigation, and incident response.

## Technologies Used
- Microsoft Sentinel
- Microsoft Defender portal
- Microsoft Azure
- Azure Monitor and Azure Activity Logs
- Log Analytics Workspace
- Kusto Query Language (KQL)
- GitHub

## Lab Architecture
Azure Subscription → Azure Activity Logs → Diagnostic Settings → Log Analytics Workspace → Microsoft Sentinel Analytics Rule → Security Alert → Incident Investigation → Resolution

## Implementation
1. Created an Azure resource group and Log Analytics workspace.
2. Configured Azure diagnostic settings to collect Administrative, Security, and Policy activity logs.
3. Enabled Microsoft Sentinel for the Log Analytics workspace.
4. Validated log ingestion using KQL queries.
5. Generated controlled test events by modifying Azure resource tags.
6. Created a custom scheduled detection rule for successful Azure resource write operations.
7. Investigated a generated security incident through Microsoft Defender.
8. Classified the incident as expected security testing activity, documented findings, and resolved it.

## Custom KQL Detection Query
```kql
AzureActivity
| where OperationNameValue endswith "/write"
| where ActivityStatusValue == "Success"
| project TimeGenerated, Caller, OperationNameValue, ResourceGroup, ResourceId, ActivityStatusValue
```

## Detection Rule Configuration
- Name: Azure Resource Modification Detection
- Severity: Medium
- Execution frequency: Every 5 hours
- Query lookback: 5 hours
- Alert threshold: More than 0 matching events
- Event grouping: Single grouped alert
- Incident creation: Enabled

## Investigation Findings
Successfully generated and investigated a Microsoft Sentinel security incident associated with authorized lab activity.

Reviewed two successful Azure administrative operations:
- Microsoft.Insights/diagnosticSettings/write
- Microsoft.Resources/tags/write

Confirmed these changes were intentionally performed as part of the home lab. The incident was classified as informational, expected activity (security testing) and resolved with documented findings.

## Results
- Verified Azure Activity log ingestion.
- Validated KQL detection logic against real Azure administrative events.
- Created and enabled one custom analytics rule.
- Generated and investigated one security incident.
- Documented and resolved the incident.
- Exported an incident investigation report for private records.

## Security and Privacy
Public screenshots and documentation should exclude personal email addresses, subscription identifiers, authentication credentials, and other sensitive cloud environment details.

## Skills Demonstrated
SIEM Administration | Cloud Security Monitoring | KQL | Detection Engineering | Log Analysis | Security Incident Investigation | Alert Triage | Incident Documentation

## Project Status
Completed hands-on implementation and investigation on October 18, 2026.
  
