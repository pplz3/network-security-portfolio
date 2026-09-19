# Incident Response Process

## 7 ขั้นตอนสำคัญในการรับมือ Cybersecurity Incident อย่างเป็นระบบ

ในโลกของ Cybersecurity คำถามสำคัญไม่ใช่เพียงว่า

> **“องค์กรจะสามารถป้องกันการโจมตีได้หรือไม่?”**

แต่ยังรวมถึง

> **“หากเกิดเหตุการณ์ขึ้น องค์กรสามารถตรวจพบ ควบคุม และกู้คืนระบบได้เร็วแค่ไหน?”**

เพราะไม่มี Security Control ใดที่สามารถป้องกัน Cybersecurity Incident ได้ 100%

ดังนั้น **Incident Response (IR)** จึงเป็นหนึ่งในความสามารถสำคัญขององค์กรในการลดผลกระทบจาก Cyber Attack และทำให้ Business สามารถกลับมาดำเนินงานได้อย่างปลอดภัย

แนวทางของ NIST เป็นหนึ่งใน Framework ที่องค์กรทั่วโลกนำมาใช้ในการออกแบบ Incident Response Process โดยในทางปฏิบัติองค์กรสามารถแตกกระบวนการออกเป็น **7 ขั้นตอน** เพื่อให้เหมาะกับการทำงานจริง

**Preparation → Detection → Analysis → Containment → Eradication → Recovery → Lessons Learned**

---

# 1. Preparation

## การเตรียมความพร้อม

Incident Response ที่ดีไม่ได้เริ่มต้นเมื่อเกิด Incident

แต่เริ่มตั้งแต่ **ก่อนเกิด Incident**

องค์กรควรเตรียมทั้ง

**People + Process + Technology**

### People

กำหนดบทบาทและความรับผิดชอบให้ชัดเจน เช่น

* Incident Response Team
* Security Team
* IT Infrastructure
* Network Team
* Application Team
* System Owner
* Management
* Compliance / Legal
* External Security Provider

รวมถึงกำหนด **Escalation Path และ Contact List**

### Process

ควรมีเอกสาร เช่น

* Incident Response Policy
* Incident Response Procedure
* Incident Classification
* Incident Severity
* Escalation Procedure
* Communication Procedure
* Evidence Handling Procedure
* Regulatory Reporting Procedure

### Technology

ควรมี Security Controls และ Monitoring ที่เหมาะสม เช่น

* SIEM
* EDR/XDR
* Firewall
* IDS/IPS
* WAF
* Vulnerability Scanner
* Email Security
* Identity Security
* Network Monitoring

นอกจากนี้ควรมีการ **Incident Response Exercise / Tabletop Exercise** เพื่อทดสอบว่าเมื่อเกิดเหตุจริง ทุกคนรู้ว่าต้องทำอะไรและใครเป็นผู้ตัดสินใจ

---

# 2. Detection & Monitoring

## การตรวจจับและเฝ้าระวัง

ขั้นตอนต่อมาคือการตรวจพบเหตุการณ์ผิดปกติ

Incident สามารถถูกตรวจพบได้จากหลายแหล่ง เช่น

* SIEM Alert
* EDR/XDR
* Firewall
* WAF
* IDS/IPS
* Authentication Logs
* VPN Logs
* Application Logs
* User Report
* Helpdesk
* Threat Intelligence

ตัวอย่างเช่น

SIEM ตรวจพบว่า User Account มีการ Login จาก IP Address ที่ผิดปกติ

หรือ EDR ตรวจพบว่ามี Process ต้องสงสัยกำลังทำงานบนเครื่อง Endpoint

สิ่งสำคัญคือ

> **ไม่ใช่ทุก Alert จะเป็น Incident**

ดังนั้น Alert ต้องถูกส่งเข้าสู่ขั้นตอน Analysis และ Triage

---

# 3. Analysis & Triage

## การวิเคราะห์และจำแนกเหตุการณ์

ขั้นตอนนี้เป็นการตอบคำถามว่า

> **“สิ่งที่ตรวจพบคือ Security Incident จริงหรือไม่?”**

ทีม Security ต้องรวบรวมข้อมูลและตรวจสอบเพิ่มเติม เช่น

* Source IP
* Destination IP
* Username
* Timestamp
* Authentication Logs
* Endpoint Logs
* Firewall Logs
* EDR Logs
* Network Traffic
* File Activity
* Process Activity

จากนั้นประเมิน

### Impact

มีระบบหรือผู้ใช้งานได้รับผลกระทบกี่ราย?

### Scope

Incident กระจายไปถึงระบบใดบ้าง?

### Severity

เป็น Low, Medium, High หรือ Critical?

### Business Impact

กระทบ Business Operation หรือ Critical System หรือไม่?

### Data Impact

มี Sensitive Data หรือ Customer Data เกี่ยวข้องหรือไม่?

ผลลัพธ์ของขั้นตอนนี้ควรนำไปสู่การตัดสินใจว่า

**False Positive → Close**

หรือ

**Confirmed Incident → Incident Response**

---

# 4. Containment

## การควบคุมและจำกัดผลกระทบ

เมื่อยืนยันว่าเป็น Incident จริง สิ่งที่ต้องทำคือ

> **หยุดการโจมตีและป้องกันไม่ให้ Incident ขยายวงกว้างขึ้น**

ตัวอย่างมาตรการ Containment ได้แก่

* Isolate Endpoint
* Disable User Account
* Block Malicious IP
* Block Malicious Domain
* Block File Hash
* Disable VPN Account
* Revoke Session
* Block C2 Communication
* Isolate Network Segment
* Disconnect Compromised Server

ตัวอย่างเช่น

พบ Endpoint ถูก Malware และกำลังเชื่อมต่อไปยัง Command & Control Server

ทีม Security อาจดำเนินการ

**EDR → Isolate Endpoint**

↓

**Firewall → Block C2 IP**

↓

**AD → Disable Account**

เพื่อป้องกันไม่ให้ Attacker สามารถดำเนินการต่อได้

---

# 5. Eradication

## การกำจัดต้นตอของปัญหา

หลังจาก Containment แล้ว ต้องกำจัด Threat และ Root Cause

ไม่ควรแก้เพียงอาการที่มองเห็น แต่ต้องค้นหาว่า

> **Attacker เข้ามาได้อย่างไร?**

ตัวอย่างเช่น

### Malware Incident

* Remove Malware
* Reimage Endpoint
* Update Security Agent
* Patch Vulnerability
* Block IOC

### Account Compromise

* Reset Password
* Revoke Session
* Revoke Token
* Enable MFA
* Review Privilege
* Remove Persistence

### Server Compromise

* Remove Backdoor
* Patch Vulnerability
* Rotate Credentials
* Review Configuration
* Validate System Integrity

เป้าหมายคือทำให้มั่นใจว่า **Threat และ Persistence Mechanism ถูกกำจัดออกจาก Environment แล้ว**

---

# 6. Recovery

## การกู้คืนระบบ

หลังจากกำจัด Threat แล้ว ต้องนำระบบกลับมาให้บริการอย่างปลอดภัย

ขั้นตอนอาจประกอบด้วย

1. Validate System Integrity
2. Restore System
3. Apply Security Patch
4. Reset Credentials
5. Validate Security Controls
6. Monitor System
7. Return to Production

สำหรับ Critical Systems ต้องพิจารณาเรื่อง

* Backup
* RPO
* RTO
* DR Site
* Failover
* Business Continuity

สิ่งสำคัญคือ

> **Recovery ไม่ใช่เพียงการทำให้ระบบกลับมาใช้งานได้ แต่ต้องทำให้ระบบกลับมาอย่างปลอดภัยด้วย**

หลังจาก Recovery ควรเพิ่ม Monitoring เพื่อเฝ้าระวังว่าการโจมตีไม่ได้กลับมาอีก

---

# 7. Post-Incident Activity

## Lessons Learned และการปรับปรุง

Incident ไม่ควรจบลงทันทีเมื่อระบบกลับมาใช้งานได้

ควรมี **Post-Incident Review**

เพื่อหาคำตอบว่า

### What happened?

เกิดอะไรขึ้น?

### How did it happen?

Attacker เข้ามาได้อย่างไร?

### What was affected?

มีระบบหรือข้อมูลใดได้รับผลกระทบ?

### What worked?

Security Control ใดสามารถช่วยตรวจจับหรือหยุด Incident?

### What did not work?

Control หรือ Process ใดที่ยังมีช่องว่าง?

### How can we prevent recurrence?

ต้องปรับปรุงอะไรเพื่อไม่ให้เกิดซ้ำ?

---

# Incident Report

หลัง Incident ควรจัดทำ **Incident Report** ซึ่งอาจประกอบด้วย

* Incident ID
* Date / Time
* Detection Source
* Incident Description
* Affected Systems
* Impact Assessment
* Timeline
* Indicators of Compromise (IOC)
* Actions Taken
* Root Cause
* Containment
* Eradication
* Recovery
* Evidence
* Communication / Escalation
* Regulatory Reporting
* Lessons Learned
* Corrective Actions

---

# Incident Timeline

หนึ่งในข้อมูลที่มีประโยชน์มากสำหรับ Incident Investigation คือ **Timeline**

ตัวอย่าง

**09:10**

SIEM Detect Suspicious Login

↓

**09:20**

Security Team Starts Investigation

↓

**09:35**

Confirmed Account Compromise

↓

**09:40**

Account Disabled

↓

**09:45**

Endpoint Isolated

↓

**10:30**

Root Cause Identified

↓

**11:30**

Eradication Completed

↓

**13:00**

System Recovery

↓

**15:00**

Enhanced Monitoring

Timeline ช่วยให้ทีมสามารถวิเคราะห์ได้ว่า

**Detection → Response → Containment → Recovery**

ใช้เวลานานเท่าใด

---

# Incident Response KPI

องค์กรสามารถใช้ KPI เพื่อวัดประสิทธิภาพของ Incident Response เช่น

| KPI                   | ความหมาย                        |
| --------------------- | ------------------------------- |
| MTTD                  | Mean Time to Detect             |
| MTTA                  | Mean Time to Acknowledge        |
| MTTC                  | Mean Time to Contain            |
| MTTR                  | Mean Time to Respond/Recover    |
| Incident Closure Rate | อัตราการปิด Incident            |
| Repeat Incident Rate  | Incident ที่เกิดซ้ำ             |
| False Positive Rate   | Alert ที่ไม่ใช่ Incident        |
| Critical Incident SLA | การตอบสนองต่อ Critical Incident |

ตัวอย่างเช่น หาก

**MTTD = 4 ชั่วโมง**

องค์กรอาจต้องกลับไปดูว่า Monitoring และ Detection Capability มีช่องว่างตรงไหน

หาก

**MTTR = 12 ชั่วโมง**

อาจต้องวิเคราะห์ว่าเกิดจาก

* Process
* Skill
* Technology
* Escalation
* Dependency
* Decision Making

หรือปัจจัยอื่นใด

---

# Incident Response กับ Digital Forensics

ใน Incident ที่มีความรุนแรงสูง การ Response ควรคำนึงถึง **Digital Forensics**

ตัวอย่าง Evidence ได้แก่

* Windows Event Logs
* Linux Logs
* Firewall Logs
* VPN Logs
* EDR Logs
* Memory
* Disk Image
* Network Traffic
* Malware Sample
* Authentication Logs

สิ่งสำคัญคือ

> **อย่ารีบ Format หรือ Reinstall ระบบที่อาจมีหลักฐานสำคัญ ก่อนพิจารณาด้าน Forensics และ Evidence Preservation**

โดยเฉพาะ Incident ที่อาจเกี่ยวข้องกับ Data Breach, Privileged Account Compromise หรือ Regulatory Investigation

---

# Incident Response ไม่ใช่หน้าที่ของ Security Team เพียงฝ่ายเดียว

Incident Response ที่มีประสิทธิภาพต้องอาศัยการทำงานร่วมกันระหว่างหลายฝ่าย

**Security**

ตรวจจับและวิเคราะห์

↓

**IT Infrastructure**

ควบคุมและกู้คืนระบบ

↓

**Network**

ควบคุม Traffic และ Network Access

↓

**Application**

ตรวจสอบ Application

↓

**Business Owner**

ประเมิน Business Impact

↓

**Management**

ตัดสินใจและกำหนดทิศทาง

↓

**Compliance / Legal**

ประเมิน Regulatory และ Legal Requirements

ดังนั้น Incident Response จึงเป็นทั้ง **Technical Process และ Business Process**

---

# Conclusion

Incident Response ที่ดีไม่ใช่เพียงการแก้ปัญหาเมื่อระบบถูกโจมตี แต่เป็นความสามารถขององค์กรในการ

**Prepare**

→ **Detect**

→ **Analyze**

→ **Contain**

→ **Eradicate**

→ **Recover**

→ **Learn**

หัวใจสำคัญคือ

> **“Detect Early, Respond Quickly, Contain Effectively, Recover Safely and Learn Continuously.”**

องค์กรที่มี Incident Response Process ที่ชัดเจน จะสามารถลดผลกระทบจาก Cybersecurity Incident ได้อย่างเป็นระบบ และที่สำคัญ ทุก Incident ควรถูกนำมาใช้เป็นข้อมูลในการปรับปรุง **Security Control, Risk Management, Governance และ Business Continuity** ให้แข็งแรงขึ้นในอนาคต
