# AWS Threat Detection Lab using GuardDuty, CloudTrail, and SNS

---

## Table of Contents
- [Overview](#overview)
- [Objectives](#objectives)
- [Architecture](#architecture)
- [CloudTrail Logging](#cloudtrail-logging)
- [GuardDuty Threat Detection](#guardduty-threat-detection)
- [IAM Attack Simulation](#iam-attack-simulation)
- [API Activity Simulation](#api-activity-simulation)
- [GuardDuty Findings](#guardduty-findings)
- [SNS Alerting Setup](#sns-alerting-setup)
- [EventBridge Integration](#eventbridge-integration)
- [Alert Validation](#alert-validation)
- [Incident Response and Remediation](#incident-response-and-remediation)
- [Conclusion](#conclusion)

---

## Overview
This project demonstrates the implementation of a **cloud threat detection and alerting system** in AWS. It simulates suspicious API activity using IAM credentials and detects it using **AWS GuardDuty**, while logging all actions through **CloudTrail**. Alerts are automatically delivered via **SNS** using **EventBridge**, replicating a real-world cloud security monitoring pipeline.

---

## Objectives
- Enable AWS CloudTrail for activity logging  
- Configure GuardDuty for threat detection  
- Simulate suspicious API activity using IAM credentials  
- Detect threats through GuardDuty findings  
- Implement real-time alerting using SNS and EventBridge  
- Demonstrate incident response and remediation practices  

---

## Architecture
The following services were used:

- **CloudTrail** → Logs all API activity  
- **GuardDuty** → Detects suspicious behavior  
- **IAM** → Simulates attacker credentials  
- **CloudShell (CLI)** → Generates API activity  
- **EventBridge** → Routes detection events  
- **SNS** → Sends real-time alerts  

---

## CloudTrail Logging
AWS CloudTrail was configured to log all management events across the account.

![CloudTrail Enabled](screenshots/cloudtrail-enabled.png)

---

## GuardDuty Threat Detection
GuardDuty was enabled to monitor CloudTrail logs and identify suspicious activity.

![GuardDuty Enabled](screenshots/guardduty-enabled.png)

---

## IAM Attack Simulation
A test IAM user (`attacker-user`) was created to simulate a compromised account.

![IAM User Created](screenshots/iam-attacker-user-created.png)

---

### Access Key Creation
An access key was generated to simulate API-based access.

Sensitive credentials have been redacted for security purposes.

![Access Key Created](screenshots/access-key-created.png)

---

## API Activity Simulation
Suspicious API activity was simulated using AWS CLI.

```bash
aws iam list-users
aws s3 ls
aws ec2 describe-instances
```

![Suspicious API Activity](screenshots/suspicious-api-activity.png)

Additional API calls were executed to increase detection likelihood:

![Multiple API Calls](screenshots/multiple-api-calls.png)

---

## GuardDuty Findings
GuardDuty successfully detected suspicious activity and generated findings.

![GuardDuty Findings](screenshots/guardduty-findings.png)

---

## SNS Alerting Setup
An SNS topic was created to send real-time alerts.

![SNS Topic Created](screenshots/sns-topic-created.png)

Email subscription was configured and confirmed:

![SNS Email Confirmed](screenshots/sns-email-confirmed.png)

---

## EventBridge Integration
An EventBridge rule was created to route GuardDuty findings to SNS.

![EventBridge Rule](screenshots/eventbridge-rule-created.png)

---

## Alert Validation
Upon generating new findings, an alert was successfully received via email.

![SNS Alert Received](screenshots/sns-alert-received.png)

---

## Incident Response and Remediation

Following detection of suspicious activity, the following response actions were implemented:

### 🔹 Immediate Actions
- Identified compromised IAM user (`attacker-user`)  
- Reviewed GuardDuty findings for context  
- Disabled or rotated exposed access keys  

---

### 🔹 Investigation
- Analyzed CloudTrail logs to trace activity  
- Identified API calls such as:
  - `ListUsers`
  - `DescribeInstances`
  - `ListBuckets`
- Reviewed source IP and metadata from GuardDuty  

---

### 🔹 Containment
- Removed excessive permissions (e.g. `AdministratorAccess`)  
- Applied least privilege principles  
- Verified no unauthorized changes were made  

---

### 🔹 Recovery
- Replaced compromised credentials  
- Enabled MFA where applicable  
- Confirmed system integrity  

---

### 🔹 Prevention and Improvements
- Implemented continuous monitoring (GuardDuty + CloudTrail)  
- Configured real-time alerting (SNS + EventBridge)  
- Recommended:
  - avoiding long-term access keys  
  - regular credential rotation  
  - IAM policy auditing  

---

## Conclusion

This project demonstrates a complete cloud security workflow, including **threat detection, monitoring, alerting, and incident response** within AWS. By integrating GuardDuty, CloudTrail, EventBridge, and SNS, a real-time security pipeline was successfully implemented.

The project highlights the importance of:
- proactive threat detection  
- automated alerting systems  
- secure IAM practices  
- structured incident response  

This hands-on implementation reflects real-world cloud security operations and provides a strong foundation for roles in **cloud security and cybersecurity engineering**.

---
