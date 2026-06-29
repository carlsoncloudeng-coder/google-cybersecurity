# Botium Toys Security Audit - Portfolio Project

This repository contains the comprehensive security audit for Botium Toys, completed as part of the Google Cybersecurity Professional Certificate program. The audit assesses existing assets, identifies security controls, and determines compliance with relevant regulations and standards.

---

## Table of Contents

- [Overview](#overview)
- [Audit Scope and Goals](#audit-scope-and-goals)
- [Risk Assessment](#risk-assessment)
- [Current Assets](#current-assets)
- [Control Categories](#control-categories)
- [Controls Assessment](#controls-assessment)
- [Compliance Assessment](#compliance-assessment)
- [Recommendations](#recommendations)

---

## Overview

**Organization.** Botium Toys

**Audit Type.** Internal IT Security Audit

**Purpose.** Assess existing assets and identify controls and compliance best practices needed to improve Botium Toys' security posture and align with NIST Cybersecurity Framework (CSF) standards.

---

## Audit Scope and Goals

### Scope

The internal IT audit will assess the following areas:

- User permissions and access controls
- Existing controls, procedures, and system protocols
- Technology currently in use
- The entire security program at Botium Toys, including employee equipment, internal networks, and systems

### Goals

The goals for the internal IT audit are:

- Adhere to the NIST Cybersecurity Framework (CSF)
- Establish policies and procedures to ensure compliance with regulations
- Fortify system controls
- Provide mitigation recommendations for vulnerabilities classified as "high risk"
- Present an overall strategy to improve the security posture of the organization

---

## Risk Assessment

### Risk Description

Currently, there is inadequate management of assets. Additionally, Botium Toys does not have all of the proper controls in place and may not be fully compliant with U.S. and international regulations and standards.

### Risk Score

**8 out of 10** - Fairly high risk due to a lack of controls and adherence to compliance best practices.

### Key Risk Findings

**Potential Impact from Loss of Assets.** Rated as **medium**, because the IT department does not know which assets would be at risk.

**Risk to Assets or Fines from Governing Bodies.** Rated as **high** because Botium Toys does not have all necessary controls in place and is not fully adhering to best practices related to compliance regulations that keep critical data private and secure.

### Specific Risk Details

- All Botium Toys employees currently have access to internally stored data, including cardholder data and customers' PII/SPII.
- Encryption is not currently used to ensure confidentiality of customers' credit card information.
- Access controls pertaining to least privilege and separation of duties have not been implemented.
- No intrusion detection system (IDS) has been installed.
- There are no disaster recovery plans in place, and the company lacks backups of critical data.
- Password policies exist but have nominal requirements, not aligned with current minimum complexity standards.
- No centralized password management system exists to enforce policy requirements.
- No regular schedule is in place for legacy system maintenance and intervention methods are unclear.

### Positive Findings

- The IT department has ensured availability and integrated controls to ensure data integrity.
- A firewall is in place that blocks traffic based on appropriately defined security rules.
- Antivirus software is installed and monitored regularly by the IT department.
- The physical location has sufficient locks, up-to-date CCTV surveillance, and functioning fire detection and prevention systems.
- A plan exists to notify E.U. customers within 72 hours of a security breach.
- Privacy policies, procedures, and processes have been developed and are enforced.

---

## Current Assets

### Asset Categories

**Employee Equipment:**
- End-user devices. desktops, laptops, smartphones
- Remote workstations
- Headsets, cables, keyboards, mice
- Docking stations
- Surveillance cameras

**On-Premises Infrastructure:**
- On-premises equipment for in-office business needs
- Internal network. protected storage of customer, vendor, and organizational data
- Firewall systems
- Antivirus software
- Legacy systems requiring human monitoring

**Systems and Services:**
- Accounting systems
- Telecommunication systems
- Database systems
- Security systems
- E-commerce systems
- Inventory management systems

**Data and Storage:**
- Data retention and storage systems
- Storefront products for retail sale (on-site and online)
- Warehouse inventory

**Other Critical Assets:**
- Internet access
- Legacy system infrastructure

---

## Control Categories

Controls within cybersecurity are grouped into three main categories. each with specific types designed to provide defense in depth.

### Administrative/Managerial Controls

Address the human component of cybersecurity. These controls include policies and procedures that define how an organization manages data and clearly define employee responsibilities in protecting the organization.

| Control Name | Control Type | Control Purpose |
|---|---|---|
| Least Privilege | Preventative | Reduce risk and overall impact of malicious insider or compromised accounts |
| Disaster recovery plans | Corrective | Provide business continuity |
| Password policies | Preventative | Reduce likelihood of account compromise through brute force or dictionary attack techniques |
| Access control policies | Preventative | Bolster confidentiality and integrity by defining which groups can access or modify data |
| Account management policies | Preventative | Manage account lifecycle, reduce attack surface, and limit overall impact from disgruntled former employees and default account usage |
| Separation of duties | Preventative | Reduce risk and overall impact of malicious insider or compromised accounts |

### Technical Controls

Solutions such as firewalls, IDS, IPS, antivirus products, and encryption. These controls can be used in various ways to meet organizational goals and objectives.

| Control Name | Control Type | Control Purpose |
|---|---|---|
| Firewall | Preventative | Filter unwanted or malicious traffic from entering the network |
| IDS/IPS | Detective | Detect and prevent anomalous traffic that matches a signature or rule |
| Encryption | Deterrent | Provide confidentiality to sensitive information |
| Backups | Corrective | Restore and recover from an event |
| Password management | Preventative | Reduce password fatigue |
| Antivirus (AV) software | Corrective | Detect and quarantine known threats |
| Manual monitoring, maintenance, and intervention | Preventative | Identify and manage threats, risks, or vulnerabilities to out-of-date systems |

### Physical Controls

Include door locks, cabinet locks, surveillance cameras, and badge readers. Used to limit physical access to assets by unauthorized personnel.

| Control Name | Control Type | Control Purpose |
|---|---|---|
| Time-controlled safe | Deterrent | Reduce attack surface and overall impact from physical threats |
| Adequate lighting | Deterrent | Deter threats by limiting "hiding" places |
| Closed-circuit television (CCTV) | Preventative/Detective | Reduce risk of certain types of events and provide post-event investigation capability |
| Locking cabinets (for network gear) | Preventative | Bolster integrity by preventing unauthorized personnel from physically accessing or modifying network infrastructure |
| Signage indicating alarm service provider | Deterrent | Deter certain types of threats by making successful attack seem unlikely |
| Locks | Deterrent/Preventative | Bolster integrity by deterring and preventing unauthorized personnel from physically accessing assets |
| Fire detection and prevention | Detective/Preventative | Detect fire and prevent damage to physical assets |

### Control Types

**Preventative Controls.** Designed to prevent an incident from occurring in the first place.

**Corrective Controls.** Used to restore an asset after an incident.

**Detective Controls.** Implemented to determine whether an incident has occurred or is in progress.

**Deterrent Controls.** Designed to discourage attacks.

---

## Controls Assessment

### Controls Assessment Checklist

| Control | Currently in Place | Explanation |
|---|---|---|
| Least Privilege | **NO** | Currently, all employees have access to customer data. Privileges need to be limited to reduce the risk of a breach. |
| Disaster recovery plans | **NO** | There are no disaster recovery plans in place. These need to be implemented to ensure business continuity. |
| Password policies | **NO** | Employee password requirements are minimal, which could allow a threat actor to more easily access secure data or other assets via employee work equipment or the internal network. |
| Separation of duties | **NO** | Needs to be implemented to reduce the possibility of fraud and access to critical data, since the company CEO currently runs day-to-day operations and manages payroll. |
| Firewall | **YES** | The existing firewall blocks traffic based on an appropriately defined set of security rules. |
| Intrusion detection system (IDS) | **NO** | The IT department needs an IDS in place to help identify possible intrusions by threat actors. |
| Backups | **NO** | The IT department needs to have backups of critical data in the case of a breach to ensure business continuity. |
| Antivirus software | **YES** | Antivirus software is installed and monitored regularly by the IT department. |
| Manual monitoring, maintenance, and intervention for legacy systems | **NO** | Legacy systems are monitored and maintained, but there is not a regular schedule in place for this task. Procedures and policies related to intervention are unclear, which could place these systems at risk of a breach. |
| Encryption | **NO** | Encryption is not currently used. Implementing it would provide greater confidentiality of sensitive information. |
| Password management system | **NO** | There is no password management system currently in place. Implementing this control would improve IT department and other employee productivity in the case of password issues. |
| Locks (offices, storefront, warehouse) | **YES** | The store's physical location, which includes the company's main offices, store front, and warehouse of products, has sufficient locks. |
| Closed-circuit television (CCTV) surveillance | **YES** | CCTV is installed and functioning at the store's physical location. |
| Fire detection/prevention (fire alarm, sprinkler system, etc.) | **YES** | Botium Toys' physical location has a functioning fire detection and prevention system. |

### Summary

**Currently in Place.** 5 out of 14 controls

**Need Implementation.** 9 out of 14 controls

---

## Compliance Assessment

### Payment Card Industry Data Security Standard (PCI DSS)

PCI DSS is an international security standard meant to ensure that organizations storing, accepting, processing, and transmitting credit card information do so in a secure environment.

**Applicability.** Botium Toys needs to adhere to PCI DSS because the organization stores, accepts, processes, and transmits credit card information both in person and online.

| Best Practice | Currently Implemented | Explanation |
|---|---|---|
| Only authorized users have access to customers' credit card information. | **NO** | Currently, all employees have access to the company's internal data. |
| Credit card information is accepted, processed, transmitted, and stored internally, in a secure environment. | **NO** | Credit card information is not encrypted and all employees currently have access to internal data, including customers' credit card information. |
| Implement data encryption procedures to better secure credit card transaction touchpoints and data. | **NO** | The company does not currently use encryption to better ensure the confidentiality of customers' financial information. |
| Adopt secure password management policies. | **NO** | Password policies are nominal and no password management system is currently in place. |

### General Data Protection Regulation (GDPR)

GDPR is a European Union general data regulation that protects the processing of EU citizens' data and their right to privacy both inside and outside EU territory. If a breach occurs and an EU citizen's data is compromised, they must be informed within 72 hours of the incident.

**Applicability.** Botium Toys needs to adhere to GDPR because the organization conducts business and collects personal information from people in the EU.

| Best Practice | Currently Implemented | Explanation |
|---|---|---|
| E.U. customers' data is kept private/secured. | **NO** | The company does not currently use encryption to better ensure the confidentiality of customers' financial information. |
| There is a plan in place to notify E.U. customers within 72 hours if their data is compromised or there is a breach. | **YES** | There is a plan to notify E.U. customers within 72 hours of a data breach. |
| Ensure data is properly classified and inventoried. | **NO** | Current assets have been inventoried and listed, but not classified. |
| Enforce privacy policies, procedures, and processes to properly document and maintain data. | **YES** | Privacy policies, procedures, and processes have been developed and enforced among IT team members and other employees as needed. |

### System and Organizations Controls (SOC Type 1, SOC Type 2)

SOC controls are designed to ensure that user data is protected and organizational objectives related to operations, financial reporting, and compliance are met.

| Best Practice | Currently Implemented | Explanation |
|---|---|---|
| User access policies are established. | **NO** | Controls of Least Privilege and separation of duties are not currently in place. All employees have access to internally stored data. |
| Sensitive data (PII/SPII) is confidential and private. | **NO** | Encryption is not currently used to better ensure the confidentiality of PII/SPII. |
| Data integrity ensures the data is consistent, complete, accurate, and has been validated. | **YES** | Data integrity is in place. |
| Data is available to individuals authorized to access it. | **NO** | While data is available to all employees, authorization needs to be limited to only the individuals who need access to it to do their jobs. |

---

## Recommendations

### Critical Controls to Implement (High Priority)

Based on the audit findings, the following controls should be implemented immediately to address high-risk vulnerabilities:

1. **Least Privilege and Access Control Policies**
   - Implement role-based access control (RBAC) to restrict employee access to only the data needed for their job functions.
   - Limit access to sensitive customer data (PII, SPII, and cardholder data) to authorized personnel only.

2. **Data Encryption**
   - Implement encryption for all credit card transactions and storage.
   - Encrypt sensitive customer data (PII/SPII) both in transit and at rest.
   - This directly addresses PCI DSS, GDPR, and SOC compliance requirements.

3. **Separation of Duties**
   - Separate the CEO's responsibilities for day-to-day operations and payroll management.
   - Implement approval workflows to reduce fraud risk.

4. **Intrusion Detection System (IDS)**
   - Deploy an IDS to detect anomalous traffic and potential intrusions.
   - Enable the IT department to respond quickly to security threats.

5. **Password Management Controls**
   - Establish robust password policies with minimum complexity requirements. at least eight characters, mix of letters, numbers, and special characters.
   - Implement a centralized password management system to improve compliance and reduce productivity issues related to password resets.

### Important Controls to Implement (High to Medium Priority)

6. **Disaster Recovery Plans and Backups**
   - Develop a comprehensive disaster recovery plan.
   - Implement regular backups of critical data to ensure business continuity.

7. **Legacy System Management**
   - Establish a regular schedule for legacy system monitoring, maintenance, and intervention.
   - Document procedures and policies for legacy system management.

8. **Data Classification and Inventory**
   - Classify existing assets by sensitivity level and criticality.
   - Maintain an updated inventory of all data assets to support compliance efforts.

### Compliance Alignment

Implementing the above controls will address gaps in compliance with:
- **PCI DSS.** Encryption, access controls, and password policies will ensure secure handling of credit card information.
- **GDPR.** Encryption, data classification, and access controls will protect EU customer data.
- **SOC Type 1 and Type 2.** User access policies and encryption will ensure data confidentiality and appropriate authorization controls.

### Expected Outcomes

Once these controls are implemented, Botium Toys will:
- Reduce the risk score from 8 to a significantly lower level.
- Achieve compliance with PCI DSS, GDPR, and SOC standards.
- Better protect customer data and organizational assets.
- Reduce the likelihood of breaches and regulatory fines.
- Improve overall security posture and align with NIST CSF best practices.

---

## Control Implementation Priority Matrix

| Control | Category | Type | Priority | Risk Reduction |
|---|---|---|---|---|
| Encryption | Technical | Deterrent | High | Very High |
| Least Privilege | Administrative | Preventative | High | Very High |
| Separation of Duties | Administrative | Preventative | High | High |
| IDS | Technical | Detective | High | High |
| Password Policies & Management | Administrative | Preventative | High | High |
| Disaster Recovery Plans | Administrative | Corrective | High | High |
| Backups | Technical | Corrective | High | High |
| Legacy System Management | Administrative | Preventative | Medium | Medium |
| Data Classification | Administrative | Preventative | Medium | Medium |

---

## Document Reference

This audit was completed using the following framework and reference documents:

- **NIST Cybersecurity Framework (CSF).** Provides the overall structure for the audit.
- **PCI DSS.** Compliance standard for organizations handling payment card information.
- **GDPR.** Compliance standard for organizations processing EU citizen data.
- **SOC Type 1 and Type 2.** Compliance frameworks for user data protection and organizational controls.

---

**Audit Completion Date.** June 26th, 2026

**Auditor.** Carlson Akaolisa

**Organization.** Botium Toys

**Status.** Recommendations pending implementation and approval by IT management and stakeholders.
