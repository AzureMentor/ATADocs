---
# required metadata

title: Azure ATP SIEM log reference | Microsoft Docs 
description: Provides samples of suspicious activity logs sent from Azure ATP to your SIEM. 
keywords:
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 07/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 3261155c-3c72-4327-ba29-c113c63a4e6d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arzinger

ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Azure ATP SIEM log reference

Azure ATP can forward security alert and monitoring alert events to your SIEM. Alerts and events are in the CEF format. This reference article provides samples of the logs sent to your SIEM.

## Sample Azure ATP security alerts in CEF format
The following fields and their values are forwarded to your SIEM:

|Detail|Explanation|
|---------|---------------|
|start|start time of the alert|
|suser|account (usually the user account) involved in the alert|
|machine account|account (usually the user account) involved in the alert|
|outcome|when relevant, a success or failure of the suspicious activity in the alert|
|msg|description of the alert|
|cnt|for alerts that have a count of the number of times that activity happened (for example, brute force has an amount of guessed passwords)|
|app |protocol used in this alert|
|externalId|event type ID Azure ATP writes to the event log that corresponds to each type of alert|
|cs#label|customer strings allowed by CEF, where cs#label is the name of the new field |
|cs#|customer strings allowed by CEF, where cs# is the value.|
|
- For example: cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa
<br> The cs1 field is the alert URL. 

- For example: cs2Label=trigger cs2=new
<br> The cs2 field identifies if the alert is new or updated.


> [!NOTE]
> If you plan to create automation or scripts for Azure ATP SIEM logs, we recommend using the **externalId** field to identify the alert type instead of using the alert name for this purpose. Alert names may occasionally be modified, while the **externalId** of each alert is permanent.  

## Azure ATP security alert unique external IDs

> [!div class="mx-tableFixed"] 

|New security alert name|Previous security alert name|Unique external ID|Severity|MITRE ATT&CK Matrix™ |
|---------|----------|---------|---------|---------|
|[Account enumeration reconnaissance](atp-reconnaissance-alerts.md#account-enumeration-reconnaissance-external-id-2003)|Reconnaissance using account enumeration|2003|Medium|Discovery|
|[Data exfiltration over SMB](atp-exfiltration-alerts.md#data-exfiltration-over-smb-external-id-2030)| NA| 2030|High|Exfiltration,<br>Lateral movement,<br>Command and control|
|[Honeytoken activity](atp-compromised-credentials-alerts.md#honeytoken-activity-external-id-2014)|Honeytoken activity|2014|Medium|Credential access,<br> Discovery|
|[Malicious request of Data Protection API master key](atp-domain-dominance-alerts.md#malicious-request-of-data-protection-api-master-key-external-id-2020)|Malicious Data Protection Private Information Request|2020|High|Credential access|
|[Network mapping reconnaissance (DNS)](atp-reconnaissance-alerts.md#network-mapping-reconnaissance-dns-external-id-2007)|Reconnaissance using DNS|2007|Medium|Discovery|
|[Remote code execution attempt](atp-domain-dominance-alerts.md#remote-code-execution-attempt-external-id-2019)|Remote code execution attempt|2019|Medium|Execution,<br> Persistence,<br> Privilege escalation,<br> Defense evasion,<br> Lateral movement|
|[Remote code execution over DNS](atp-lateral-movement-alerts.md#remote-code-execution-over-dns-external-id-2036)|NA|2036|Medium|Privilege escalation,<br> Lateral movement|
|[Security principal reconnaissance (LDAP)](atp-reconnaissance-alerts.md#security-principal-reconnaissance-ldap-external-id-2038)|NA|2038|Medium|Credential access|
|[Suspected brute force attack (Kerberos, NTLM)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-kerberos-ntlm-external-id-2023)|Suspicious authentication failures|2023|Medium|Credential access|
|[Suspected brute force attack (LDAP)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-ldap-external-id-2004)|Brute force attack using LDAP simple bind|2004|Medium|Credential access|
|[Suspected brute force attack (SMB)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-smb-external-id-2033)|Unusual protocol implementation (potential use of malicious tools such as Hydra)|2033|Medium|Lateral movement|
|[Suspected DCShadow attack (domain controller promotion)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-promotion-external-id-2028)|Suspicious domain controller promotion (potential DCShadow attack)|2028|High|Defense evasion|
|[Suspected DCShadow attack (domain controller replication request)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-replication-request-external-id-2029)|Suspicious domain controller replication request (potential DCShadow attack)|2029|High|Defense evasion|
|[Suspected DCSync attack (replication of directory services)](atp-domain-dominance-alerts.md#suspected-dcsync-attack-replication-of-directory-services-external-id-2006)|Malicious replication of directory services|2006|High|Persistence,<br> Credential access|
|[Suspected Golden Ticket usage (encryption downgrade)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-encryption-downgrade-external-id-2009)|Encryption downgrade activity (potential golden ticket attack)|2009|Medium|Privilege Escalation,<br> Lateral movement,<br>Persistence|
|[Suspected Golden Ticket usage (forged authorization data)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-forged-authorization-data-external-id-2013)|Privilege escalation using forged authorization data|2013|High|Privilege escalation,<br>Lateral movement,<br>Persistence|
|[Suspected Golden Ticket usage (nonexistent account)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-nonexistent-account-external-id-2027)|Kerberos Golden Ticket - nonexistent account|2027|High|Privilege Escalation,<br> Lateral movement,<br>Persistence|
|[Suspected Golden Ticket usage (ticket anomaly)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-external-id-2032)|NA|2032|High|Privilege Escalation,<br> Lateral movement,<br>Persistence|
|[Suspected Golden Ticket usage (time anomaly)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-time-anomaly-external-id-2022)|Kerberos Golden Ticket - time anomaly|2022|High|Privilege Escalation,<br> Lateral movement,<br>Persistence|
|[Suspected identity theft (pass-the-hash)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-hash-external-id-2017)|Identity theft using Pass-the-Hash attack|2017|High|Lateral movement|
|[Suspected identity theft (pass-the-ticket)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-ticket-external-id-2018)|Identity theft using Pass-the-Ticket attack|2018|High or Medium|Lateral movement|
|[Suspected NTLM authentication tampering](atp-lateral-movement-alerts.md#suspected-ntlm-authentication-tampering-external-id-2039)|NA|2039|Medium|Privilege escalation,<br> Lateral movement|
|[Suspected NTLM relay attack](atp-lateral-movement-alerts.md#suspected-ntlm-relay-attack-exchange-account-external-id-2037)|NA|2037|Medium or Low if observed using signed NTLM v2 protocol|Privilege escalation, <br> Lateral movement|
|[Suspected over-pass-the-hash attack (encryption downgrade)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-encryption-downgrade-external-id-2008)|Encryption downgrade activity (potential overpass-the-hash attack)|2008|Medium|Lateral movement|
|[Suspected overpass-the-hash attack (Kerberos)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-kerberos-external-id-2002)|Unusual Kerberos protocol implementation (potential overpass-the-hash attack)|2002|Medium|Lateral movement|
|[Suspected skeleton key attack (encryption downgrade)](atp-domain-dominance-alerts.md#suspected-skeleton-key-attack-encryption-downgrade-external-id-2010)|Encryption downgrade activity (potential skeleton key attack)|2010|Medium|Lateral movement,<br> Persistence|
|[Suspected use of Metasploit hacking framework](atp-compromised-credentials-alerts.md#suspected-use-of-metasploit-hacking-framework-external-id-2034)|Unusual protocol implementation (potential use of Metasploit hacking tools)|2034|Medium|Lateral movement|
|[Suspected WannaCry ransomware attack](atp-compromised-credentials-alerts.md#suspected-wannacry-ransomware-attack-external-id-2035)|Unusual protocol implementation (potential WannaCry ransomware attack)|2035|Medium|Lateral movement|
|[Suspicious communication over DNS](atp-exfiltration-alerts.md#suspicious-communication-over-dns-external-id-2031)|Suspicious communication over DNS|2031|Medium|Exfiltration|
|[Suspicious additions to sensitive groups](atp-domain-dominance-alerts.md#suspicious-additions-to-sensitive-groups-external-id-2024)|Suspicious additions to sensitive groups|2024|Medium|Credential access,<br>Persistence|
|[Suspicious service creation](atp-domain-dominance-alerts.md#suspicious-service-creation-external-id-2026)|Suspicious service creation|2026|Medium|Execution,<br> Persistence,<br> Privilege Escalation,<br> Defense evasion,<br>Lateral movement|
|[Suspicious VPN connection](atp-compromised-credentials-alerts.md#suspicious-vpn-connection-external-id-2025)|Suspicious VPN connection|2025|Medium|Persistence,<br>Defense evasion|
|[User and group membership reconnaissance (SAMR)](atp-reconnaissance-alerts.md#user-and-group-membership-reconnaissance-samr-external-id-2021)|Reconnaissance using directory services queries|2021|Medium|Discovery|
|[User and IP address reconnaissance (SMB)](atp-reconnaissance-alerts.md#user-and-ip-address-reconnaissance-smb-external-id-2012)|Reconnaissance using SMB Session Enumeration|2012|Medium|Discovery|
|

## Sample logs

The log examples comply with RFC 5242, but Azure ATP also supports RFC 3164.

Priorities:

- 3=Low
- 5=Medium
- 10=High

### Account enumeration reconnaissance 
02-21-2018	16:19:35	Auth.Warning	192.168.0.220	1 2018-02-21T14:19:27.540731+00:00 CENTER CEF 6076 AccountEnumerationSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AccountEnumerationSecurityAlert|Reconnaissance using account enumeration|5|start=2018-02-21T14:19:02.6045416Z app=Kerberos shost=CLIENT1 suser=LMaldonado msg=Suspicious account enumeration activity using the Kerberos protocol, originating from CLIENT1, was observed and successfully guessed Lamon Maldonado (Software Engineer). externalId=2003 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/eb6a35da-ff7f-4ab5-a1b5-a07529a89e6d cs2Label=trigger cs2=new

### Data exfiltration over SMB
12-19-2018  14:17:46    Auth.Error     127.0.0.1      1 2018-12-19T12:17:34.645993+00:00 DC1 CEF 3288 SmbDataExfiltrationSecurityAlert ï»¿0|Microsoft|Azure ATP|2.60.0.0|SmbDataExfiltrationSecurityAlert|[PREVIEW] Data exfiltration over SMB|10|start=2018-12-19T12:14:12.4932821Z app=Smb shost=CLIENT1 msg=Eugene Jenkins (Software Engineer) on DC2 copied suspicious files to CLIENT1. externalId=2030 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/3ca2ec9d-2c67-44cc-a2d6-391716611bb6 cs2Label=trigger cs2=new

### Honeytoken activity
02-21-2018	16:20:36	Auth.Warning  192.168.0.220	1 2018-02-21T14:20:34.106162+00:00 CENTER CEF 6076 HoneytokenActivitySecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|HoneytokenActivitySecurityAlert|Honeytoken activity|5|start=2018-02-21T14:20:26.6705617Z app=Kerberos suser=honey msg=The following activities were performed by honey:\r\nLogged in to CLIENT2 via DC1. externalId=2014 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/9249fe9a-c883-46dd-a4da-2a1fca5f211c cs2Label=trigger cs2=new

### Malicious request of Data Protection API master key 
10-29-2018	11:22:04	Auth.Error	192.168.0.202	1 2018-10-29T09:22:00.350864+00:00 DC3 CEF 3908 RetrieveDataProtectionBackupKeyS ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|RetrieveDataProtectionBackupKeySecurityAlert|Malicious Data Protection Private Information Request|10|start=2018-10-29T09:19:45.6307993Z app=LsaRpc shost=CLIENT1 msg=user1 performed 1 successful attempts from CLIENT1 to retrieve DPAPI domain backup key from DC1. externalId=2020 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/2f5717cb-2434-4d54-8af4-b2c6d14bc15c cs2Label=trigger cs2=new

### Network-mapping reconnaissance (DNS)
10-29-2018	11:20:02	Auth.Warning	192.168.0.202	1 2018-10-29T09:19:59.056894+00:00 DC3 CEF 3908 DnsReconnaissanceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|DnsReconnaissanceSecurityAlert|Reconnaissance using DNS|5|start=2018-10-29T09:19:43.5033765Z app=Dns shost=CLIENT1 msg=Suspicious DNS activity was observed, originating from CLIENT1 (which is not a DNS server) against DC1. externalId=2007 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/23937d33-ff71-484d-be0a-3c417fe573ce cs2Label=trigger cs2=new

### Reconnaissance using directory services queries 
02-21-2018	16:22:08	Auth.Warning	192.168.0.220	1 2018-02-21T14:21:54.267658+00:00 CENTER CEF 6076 SamrReconnaissanceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|SamrReconnaissanceSecurityAlert| Reconnaissance using directory services enumeration |5|start=2018-02-21T14:19:41.9912772Z app= Samr shost=CLIENT1 suser=user1 outcome=Success msg= The following directory services enumerations using SAMR protocol were attempted against DC1 from CLIENT1:\r\nSuccessful enumeration of all groups in domain1.test.local by user1. externalId=2019 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f295029a-ffae-408b-9dd0-55424c81eac0 cs2Label=trigger cs2=new

### Remote code execution attempt
10-29-2018	11:22:04	Auth.Warning	192.168.0.202	1 2018-10-29T09:22:00.100856+00:00 DC3 CEF 3908 RemoteExecutionSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|RemoteExecutionSecurityAlert|Remote code execution attempt|5|start=2018-10-29T09:19:45.0552367Z shost=CLIENT1 msg=The following remote code execution attempts were performed on DC1 from CLIENT1:\r\nSuccessful remote scheduling of one or more tasks by user1.\r\nFailed remote scheduling of one or more tasks by user1.\r\nSuccessful remote execution of one or more WMI methods by user1. externalId=2019 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f063c778-830c-4e9f-98d1-bc6c11c94e11 cs2Label=trigger cs2=new

### Remote code execution over DNS
1-17-2019	08:24:54	Auth.Warning	192.168.0.202	1 2019-01-17T08:24:54.100856+00:00 DC3 CEF 3908 DnsRemoteCodeExecutionSecurityAlert ï»¿0|Microsoft|Azure ATP|2.63.0.0|DnsRemoteCodeExecutionSecurityAlert|[PREVIEW] Remote code execution over DNS|5|start=2019-01-17T08:24:54.5293800Z app=Dns shost=CLIENT1 msg=An actor attempted to run commands remotely on CLIENT1 from DC1, over DNS protocol. externalId=2036 cs1Label=url cs1=https\:////contoso-corp.atp.azure.com:13000/securityAlert/591f9769-d904-40b1-89fa-c307c2ca814f cs2Label=trigger cs2=new

### Security principal reconnaissance (LDAP)
02-18-2019  16:48:08 Auth.Warning  127.0.0.1  1 2019-02-18T14:48:02.912264+00:00 DC1 CEF 4656 LdapSearchReconnaissanceSecurity ï»¿0|Microsoft|Azure ATP|2.66.0.0|LdapSearchReconnaissanceSecurityAlert|[PREVIEW] Reconnaissance using LDAP Queries|5|start=2019-02-18T14:46:29.4644276Z app=LdapSearch shost=CLIENT1 msg=An actor on CLIENT1 sent suspicious LDAP queries to DC1, searching for 4 types of enumeration and Server Operators (Members can administer domain servers) in 2 domains externalId=2038 cs1Label=url cs1=https\://contoso-corp.atp.azure..com:13000/securityAlert/81ea99c4-ce1f-4581-ac8f-7440fbed7cd0 cs2Label=trigger cs2=new

### Suspected brute force attack (LDAP)
02-21-2018	16:20:21	Auth.Warning	192.168.0.220	1 2018-02-21T14:20:06.156238+00:00 CENTER CEF 6076 LdapBruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|LdapBruteForceSecurityAlert|Brute force attack using LDAP simple bind|5|start=2018-02-21T14:19:41.7422810Z app=Ldap suser=Wofford Thurston shost=CLIENT1 msg=A brute force attack using the Ldap protocol was attempted on Wofford Thurston (Software Engineer) from CLIENT1 (100 guess attempts). cnt=100 externalId=2004 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/57b8ac96-7907-4971-9b27-ec77ad8c029a cs2Label=trigger cs2=update

### Suspected brute force attack (Kerberos, NTLM)
10-29-2018	11:20:47	Auth.Warning	192.168.0.202	1 2018-10-29T09:20:44.478827+00:00 DC3 CEF 3908 BruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|BruteForceSecurityAlert|Suspicious authentication failures|5|start=2018-10-29T09:19:44.9512286Z app=Kerberos shost=CLIENT1 msg=Suspicious authentication failures indicating a potential brute-force attack were detected from CLIENT1. externalId=2023 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/85042c8e-27fa-49b3-8667-dabc1aa31580 cs2Label=trigger cs2=new

### Suspected DCSync attack (replication of directory services)
02-21-2018	16:20:06	Auth.Warning	192.168.0.220	1 2018-02-21T14:19:54.254930+00:00 CENTER CEF 6076 MaliciousServiceCreationSecurity ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|MaliciousServiceCreationSecurityAlert|Suspicious service creation|5|start=2018-02-21T14:19:41.7897808Z app=ServiceInstalledEvent shost=CLIENT1 msg=user1 created MaliciousService in order to execute potentially malicious commands on CLIENT1. externalId=2026 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/179229b6-b791-4895-b5aa-fdf3747a325c cs2Label=trigger cs2=update

### Suspected Golden Ticket usage (encryption downgrade)
10-29-2018	11:25:07	Auth.Warning	192.168.0.202	1 2018-10-29T09:25:01.007701+00:00 DC3 CEF 3908 GoldenTicketEncryptionDowngradeS ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|GoldenTicketEncryptionDowngradeSecurityAlert|Encryption downgrade activity (potential golden ticket attack)|5|start=2018-10-29T09:37:49.0849130Z app=Kerberos msg=W10-000007-Lap used a weaker encryption method (RC4),Â in the Kerberos service request (TGS_REQ),Â from W10-000007-Lap, to access host/domain1.test.local. externalId=2009 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f01f8403-88b2-437e-b4ad-d72485fe05ac cs2Label=trigger cs2=new

### Suspected Golden Ticket usage (non-existent account)
07-01-2018  14:28:49    Auth.Error  192.168.0.100   1 2018-07-01T11:28:35.546638+00:00 CENTER CEF 38768 ForgedPrincipalSecurityAlert ï»¿0|Microsoft|Azure ATP|2.39.0.0|ForgedPrincipalSecurityAlert|Kerberos Golden Ticket - non-existing account|10|start=2018-07-01T09:48:31.2567987Z app=Kerberos suser=domain1.test.local\fake msg=domain1.test.local\fake, which does not exist in Active Directory, used a Kerberos ticket. The ticket was detected from 2 computers to access 3 resources. This may indicate a potential Golden Ticket attack. externalId=2027 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/98f050d4-9134-429c-8e54-d8eeb19849c4 cs2Label=trigger cs2=update

### Suspected Golden Ticket usage (ticket anomaly) 
1 2018-11-18T10:46:23.346946+00:00 MAXIMG-7050 CEF 24284 GoldenTicketSizeAnomalySecurityA 0|Microsoft|Azure ATP|2.56.0.0|GoldenTicketSizeAnomalySecurityAlert|[PREVIEW] Suspected Golden Ticket usage (ticket anomaly)|10|start=2018-11-18T10:44:12.9317797Z app=Kerberos shost=CLIENT2 suser=RFosdyke msg=Renzo Fosdyke (Software Engineer) used a suspicious Kerberos ticket from CLIENT2 to access ldap/domain1.test.local. externalId=2032 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/63600e03-f423-49bf-a92d-4010e1d52b9f cs2Label=trigger cs2=update

### Suspected Golden Ticket usage (time anomaly) 
02-21-2018	16:22:39	Auth.Error	192.168.0.220	1 2018-02-21T14:22:34.274054+00:00 CENTER CEF 6076 GoldenTicketSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|GoldenTicketSecurityAlert|Kerberos Golden Ticket activity|10|start=2018-02-21T14:19:03.2416152Z app=Kerberos suser=Lanell Campos msg=Suspicious usage of Lanell Campos (Software Engineer)'s Kerberos ticket, indicating a potential Golden Ticket attack, was detected. externalId=2022 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/702c836e-6f49-4479-9892-80e8bccbfac0 cs2Label=trigger cs2=update

### Suspected Golden Ticket usage (forged authorization data) 
10-29-2018	11:22:04	Auth.Error	192.168.0.202	1 2018-10-29T09:21:59.288337+00:00 DC3 CEF 3908 ForgedPacSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|ForgedPacSecurityAlert|Privilege escalation using forged authorization data|10|start=2018-10-29T09:19:43.6403358Z app=Kerberos suser=user1 msg=user1 failed to escalate privileges against DC1 to host/domain1.test.local from CLIENT1 by using forged authorization data. externalId=2013 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/b698d438-5013-4bca-be0b-f219f8b69108 cs2Label=trigger cs2=new

### Suspected identity theft (Pass-the-Hash)
02-21-2018	17:04:47	Auth.Error	192.168.0.220	1 2018-02-21T15:04:33.537583+00:00 CENTER CEF 6076 PassTheHashSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|PassTheHashSecurityAlert|Identity theft using Pass-the-Hash attack|10|start=2018-02-21T15:02:22.2577465Z app=Kerberos suser=Eugene Jenkins msg=Eugene Jenkins (Software Engineer)'s hash was stolen from one of the computers previously logged into by Eugene Jenkins (Software Engineer) and used from CLIENT1. externalId=2017 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd cs2Label=trigger cs2=update

### Suspected identity theft (Pass-the-Ticket) 
02-21-2018	17:04:47	Auth.Error	192.168.0.220	1 2018-02-21T15:04:33.537583+00:00 CENTER CEF 6076 PassTheTicketSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|PassTheTicketSecurityAlert|Identity theft using Pass-the-Ticket attack|10|start=2018-02-21T15:02:22.2577465Z app=Kerberos suser=Eugene Jenkins msg=Eugene Jenkins (Software Engineer)'s Kerberos tickets were stolen from Admin-PC to Victim-PC and used to access krbtgt/DOMAIN1.TEST.LOCAL. externalId=2018 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd cs2Label=trigger cs2=new

### Suspected NTLM authentication tampering
07-17-2019  18:18:44    Auth.Warning   192.168.0.77       1 2019-07-09T15:18:30.967118+00:00 CENTER CEF 7144 AbnormalNtlmSigningSecurityAlert ï»¿0|Microsoft|Azure ATP|2.86.0.0|AbnormalNtlmSigningSecurityAlert|[PREVIEW] Suspected NTLM authentication tampering|5|start=2019-07-09T15:14:57.5280720Z app=Ntlm shost=CLIENT1 msg=2 accounts on CLIENT1 is suspiciously trying to authenticate against 2 computers over NTLM. externalId=2039 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/d4ce6252-2c0f-47f6-a534-47ee8ad983be cs2Label=trigger cs2=new

### Suspected Over-Pass-the-Hash attack (encryption downgrade) 
02-21-2018	16:21:07	Auth.Warning	192.168.0.220	1 2018-02-21T14:20:54.145833+00:00 CENTER CEF 6076 EncryptionDowngradeSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EncryptionDowngradeSecurityAlert|Encryption downgrade activity|5|start=2018-02-21T14:19:41.8737870Z app=Kerberos msg= The encryption method of the Encrypted_Timestamp field of AS_REQ message from CLIENT1 has been downgraded based on previously learned behavior. This may be a result of a credential theft using Overpass-the-Hash from CLIENT1. externalId=2008 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2 cs2Label=trigger cs2=update

### Suspected Skeleton Key attack (encryption downgrade) 
02-21-2018	16:21:07	Auth.Warning	192.168.0.220	1 2018-02-21T14:20:54.145833+00:00 CENTER CEF 6076 EncryptionDowngradeSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EncryptionDowngradeSecurityAlert|Encryption downgrade activity|5|start=2018-02-21T14:19:41.8737870Z app=Kerberos msg=The encryption method of the ETYPE_INFO2 field of KRB_ERR message from CLIENT1 has been downgraded based on previously learned behavior. This may be a result of a Skeleton Key on DC1. externalId=2010 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2 cs2Label=trigger cs2=new

### Suspicious authentication failures
02-21-2018	16:19:20	Auth.Warning	192.168.0.220	1 2018-02-21T14:19:15.397995+00:00 CENTER CEF 6076 BruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|BruteForceSecurityAlert|Suspicious authentication failures|5|start=2018-02-21T14:19:03.3831122Z app=Kerberos shost=CLIENT1 msg=Suspicious authentication failures indicating a potential brute-force attack were detected from CLIENT1. externalId=2023 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/fea88fc7-4110-454d-816d-349032474fd6 cs2Label=trigger cs2=new

### Suspicious communication over DNS
10-04-2018  14:49:38    Auth.Warning    192.168.0.202   1 2018-10-04T11:49:25.954059+00:00 DC3 CEF 3604 DnsSuspiciousCommunicationSecuri ï»¿0|Microsoft|Azure ATP|2.49.5589.58606|DnsSuspiciousCommunicationSecurityAlert|Suspicious Communication over DNS|5|start=2018-10-04T11:49:11.0822077Z app=DnsEvent dhost= suspiciousdomainname msg=CLIENT1 sent suspicious DNS queries resolving suspiciousdomainname externalId=2031 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/0fc77777-49ca-40b3-a7ba-7644f355539e cs2Label=trigger cs2=new

### Suspicious domain controller promotion (potential DcShadow attack)
07-12-2018  11:18:07    Auth.Error  192.168.0.200    1 2018-07-12T08:18:06.883880+00:00 DC1 CEF 3868 DirectoryServicesRoguePromotionS ï»¿0|Microsoft|Azure ATP|2.40.0.0|DirectoryServicesRoguePromotionSecurityAlert| **Suspicious domain controller promotion (potential DcShadow attack)**|10|start=2018-07-12T08:17:55.4067092Z app=Ldap shost=CLIENT1 msg=CLIENT1, which is a computer in domain1.test.local, registered as a domain controller on DC1. externalId=2028 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/97c59b43-dc18-44ee-9826-8fd5d03bd53 cs2Label=trigger cs2=update

### Suspicious additions to sensitive groups
10-29-2018	11:21:03	Auth.Warning	192.168.0.202	1 2018-10-29T09:20:49.667014+00:00 DC3 CEF 3908 AbnormalSensitiveGroupMembership ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|AbnormalSensitiveGroupMembershipChangeSecurityAlert|Suspicious modification of sensitive groups|5|start=2018-10-29T09:19:43.3013729Z app=GroupMembershipChangeEvent suser=user1 msg=user1 has uncharacteristically modified sensitive group memberships. externalId=2024 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6f7e677e-f068-41e5-bada-708cd5a322b9 cs2Label=trigger cs2=new

### Suspicious replication of directory services
02-21-2018	16:21:22	Auth.Error	192.168.0.220	1 2018-02-21T14:21:13.978554+00:00 CENTER CEF 6076 DirectoryServicesReplicationSecu ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|DirectoryServicesReplicationSecurityAlert|Malicious replication of directory services|10|start=2018-02-21T14:19:03.9975656Z app=Drsr shost=CLIENT1 msg=Malicious replication requests were successfully performed by user1, from CLIENT1 against DC1. outcome=Success externalId=2006 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/cb95648e-1b6f-4d3b-81b9-7605532787d7 cs2Label=trigger cs2=new

### Suspicious replication request (potential DcShadow attack)
07-12-2018  11:18:37    Auth.Error  192.168.0.200    1 2018-07-12T08:18:32.265989+00:00 DC1 CEF 3868 DirectoryServicesRogueReplicatio ï»¿0|Microsoft|Azure ATP|2.40.0.0|DirectoryServicesRogueReplicationSecurityAlert| **Suspicious replication request (potential DcShadow attack)**|10|start=2018-07-12T08:17:55.3816102Z **app=Replication Activity** shost=CLIENT1 msg=CLIENT1, which is not a valid domain controller in domain1.test.local, sent changes to directory objects on DC1. externalId=2029 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/1d5d1444-12cf-4db9-be48-39ebc2f51515 cs2Label=trigger cs2=new

### Suspicious service creation 
10-29-2018	11:20:02	Auth.Warning	192.168.0.202	1 2018-10-29T09:19:59.164874+00:00 DC3 CEF 3908 MaliciousServiceCreationSecurity ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|MaliciousServiceCreationSecurityAlert|Suspicious service creation|5|start=2018-10-29T09:19:44.9471965Z app=ServiceInstalledEvent shost=CLIENT1 msg=user1 created MaliciousService in order to execute potentially malicious commands on CLIENT1. externalId=2026 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/118bbe3d-fe72-40de-80d0-2678b68aa027 cs2Label=trigger cs2=new

### Suspicious VPN Connection
07-03-2018  13:13:12    Auth.Warning  192.168.0.200   1 2018-07-03T10:13:06.187834+00:00 DC1 CEF 2520 AbnormalVpnSecurityAlert ï»¿0|Microsoft|Azure ATP|2.39.0.0|AbnormalVpnSecurityAlert|Suspicious VPN Connection|5|start=2018-06-30T15:34:05.3887333Z app=VpnConnection suser=user1 msg=user1 connected to a VPN using 3 computers from 3 Locations.     externalId=2025 cs1Label=url cs1=https\://contoso-corp.eng.atp.azure.com:13000/securityAlert/88c46b0e-372f-4c06-9935-67bd512c4f68 cs2Label=trigger cs2=new

### Suspected WannaCry ransomware attack
02-21-2018	16:21:22	Auth.Warning	192.168.0.220	1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|SuspectedWannaCryRansomwareAttack|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=There were attempts to authenticate from CLIENT2 against DC1 using an unusual protocol implementation. May be a result of malicious tools used to execute attacks such as WannaCry. externalId=2035 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### Suspected brute force attack (SMB)
002-21-2018	16:21:22	Auth.Warning	192.168.0.220	1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|SuspectedBrutForceAttack|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=There were attempts to authenticate from CLIENT2 against DC1 using an unusual protocol implementation. May be a result of malicious tools used to execute attacks such as Hydra. externalId=2033 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### Suspected use of Metasploit hacking framework
002-21-2018	16:21:22	Auth.Warning	192.168.0.220	1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|SuspectedAttackUsingMetasploit|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=There were attempts to authenticate from CLIENT2 against DC1 using an unusual protocol implementation. May be a result of malicious tools used to execute attacks such as Metasploit. externalId=2034 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### Suspected overpass-the-hash attack (Kerberos)
002-21-2018	16:21:22	Auth.Warning	192.168.0.220	1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|SuspectedOverPassTheHashAttack|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=There were attempts to authenticate from CLIENT2 against DC1 using an unusual protocol implementation. May be a result of malicious acts using the Kerberos protocol. externalId=2002 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### User and IP address reconnaissance (SMB) 
002-21-2018	16:21:22	Auth.Warning	192.168.0.220	1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|ReconnaissanceusingSMBSessionEnumeration|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=There were attempts to authenticate from CLIENT2 against DC1 using an unusual protocol implementation. May be a result of malicious tools used to execute attacks such as Metasploit. externalId=2034 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

## See Also
- [Azure ATP prerequisites](atp-prerequisites.md)
- [Azure ATP capacity planning](atp-capacity-planning.md)
- [Configure event collection](configure-event-collection.md)
- [Configuring Windows event forwarding](configure-event-forwarding.md)
- [Check out the Azure ATP forum!](https://aka.ms/azureatpcommunity)
