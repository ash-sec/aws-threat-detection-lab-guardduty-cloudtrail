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
