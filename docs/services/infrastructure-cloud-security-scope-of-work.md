# Infrastructure, Cloud & Security — Scope of Work Templates

> ชุดตัวอย่างขอบเขตงาน (Reusable SOW Templates) สำหรับนำไปปรับใช้กับโครงการขององค์กร
> ระยะเวลาเป็นตัวอย่าง Effort (Man-days / Man-hours) เพื่อใช้ประมาณการเบื้องต้น ไม่ใช่จำนวนวันตามปฏิทิน

## สรุปโครงการ

| # | โครงการ | ระยะเวลา |
|---:|---|---:|
| 1 | Windows Server 2016 Migration Assessment & Roadmap | 6 Man-days |
| 2 | Windows Server 2016 Migration Implementation | TBD ตามขอบเขต |
| 3 | Service Account Security Assessment & Remediation | 6 Man-days |
| 4 | Linux Platform Management, Standardization & Security | 7.5 Man-days |
| 5 | AWS Identity & Access Governance and Security Baseline | 6 Man-days |
| 6 | Microsoft 365 Security Baseline & Secure Score Improvement | 5 Man-days |
| 7 | Microsoft 365 Zero Trust – Regulatory & Compliance Readiness  | 6 Man-days |
| 8 | Microsoft 365 Zero Trust – Secure AI Apps & Data  | 6 Man-days |
| 9 | Enterprise MCP Server Implementation & Integration | 6 Man-days |
| 10 | Professional Support | 100 ชั่วโมง |

## รายละเอียด Scope of Work

### 01. Windows Server 2016 Migration Assessment & Roadmap

**รายละเอียดโดยย่อ:** ประเมินความพร้อมและจัดทำแผนย้าย Windows Server 2016 ไปยัง Windows Server 2022/2025

**Scope:** สำรวจ Server, Application และ Dependency ตามรายการที่ตกลง ประเมินความเสี่ยงและความซับซ้อน พร้อมกำหนด Target Baseline, Migration Approach และ Migration Waves; ไม่รวมการย้ายระบบจริง

**รายการที่จะดำเนินการ**

1. Kickoff และรวบรวม Server Inventory  (1 วัน)
2. วิเคราะห์ Application, Dependency และ Compatibility  (2 วัน)
3. กำหนด Target Platform, Baseline และ Migration Approach  (1 วัน)
4. จัดทำ Risk Register, Migration Waves และ Roadmap  (2 วัน)

**Deliverables:** Server/Workload Inventory, Dependency & Risk Assessment, Migration Strategy และ Roadmap

**ระยะเวลา:** 6 Man-days

**ข้อจำกัด/เงื่อนไข:** อาศัยข้อมูลจากทีม System/Application Owner; ไม่รวมการทดสอบย้ายระบบจริง

### 02. Windows Server 2016 Migration Implementation

**รายละเอียดโดยย่อ:** ดำเนินการย้าย Windows Server 2016 ตาม Migration Waves และแผน Cutover ที่ได้รับอนุมัติ

**Scope:** Pilot Migration, การย้ายระบบตาม Wave, Configuration/Functional Validation, Cutover, Remediation และการเลิกใช้ Server เดิมที่ตกลงร่วมกัน

**รายการที่จะดำเนินการ**

1. จัดทำแผน Runbook, Rollback และ Pilot Migration
2. ดำเนินการ Migration ตาม Wave ที่ตกลง
3. ทดสอบ Service, Application และ Dependency ร่วมกับ Owner
4. Cutover, Hypercare และแก้ไขปัญหาหลังย้าย
5. Decommission ระบบเดิมที่ผ่านเกณฑ์อนุมัติ

**Deliverables:** Migration Runbook, ผลทดสอบ/ผล Cutover และรายการ Server ที่ย้ายเสร็จ

**ระยะเวลา:** TBD ตามขอบเขต

**ข้อจำกัด/เงื่อนไข:** Effort เป็น TBD ต้องประเมินจำนวน Server, Application, Dependency, Downtime และ Cutover Window ก่อน

### 03. Service Account Security Assessment & Remediation

**รายละเอียดโดยย่อ:** ตรวจสอบ Service Account และลดความเสี่ยงจากสิทธิ์เกินจำเป็นหรือการตั้งค่าที่ไม่ปลอดภัย

**Scope:** ครอบคลุม AD DS/Windows Service Accounts และข้อมูลจากเครื่องมือ Identity Security (หากมี) ตามระบบที่ตกลง พร้อม Remediation เฉพาะรายการที่ได้รับอนุมัติ

**รายการที่จะดำเนินการ**

1. สำรวจ Account, Owner, Usage และ Dependency  (1.5 วัน)
2. วิเคราะห์ Privilege, Logon Rights และ Security Risks  (1.5 วัน)
3. จัดระดับความเสี่ยงและจัดทำ Remediation Plan  (1 วัน)
4. ปรับสิทธิ์/Configuration หรือ Pilot gMSA ตามความเหมาะสม  (1.5 วัน)
5. Validate และสรุปผล/รายการคงค้าง  (0.5 วัน)

**Deliverables:** Service Account Inventory, Risk Register, Remediation Checklist และ Validation Results

**ระยะเวลา:** 6 Man-days

**ข้อจำกัด/เงื่อนไข:** ไม่รวมการแก้ไข Service Account ทุกระบบทั้งองค์กร; การเปลี่ยน Credential ต้องผ่าน Change Approval

### 04. Linux Platform Management, Standardization & Security

**รายละเอียดโดยย่อ:** กำหนดมาตรฐานการบริหารและความปลอดภัยของ Linux พร้อมติดตั้งตัวอย่างอ้างอิง

**Scope:** กำหนด Standard Build/Hardening ครอบคลุม Identity, SSH/Sudo, Patching, EDR, Logging, Monitoring และ Backup พร้อม Reference Configuration บน Linux ที่ตกลง

**รายการที่จะดำเนินการ**

1. สำรวจ Linux Landscape และ Current Configuration  (1 วัน)
2. ออกแบบ Standard Build, Access และ Security Baseline  (2 วัน)
3. Implement Reference Configuration และ Integration ที่มีอยู่  (2.5 วัน)
4. Validate, จัดทำ Operation Guideline และ Knowledge Transfer  (2 วัน)

**Deliverables:** Linux Standard Baseline, Reference Build/Configuration และ Operations Checklist

**ระยะเวลา:** 7.5 Man-days

**ข้อจำกัด/เงื่อนไข:** เป็นการกำหนดมาตรฐานและทำ Reference Implementation; ไม่รวม Fleet-wide Rollout

### 05. AWS Identity & Access Governance and Security Baseline

**รายละเอียดโดยย่อ:** ประเมินและยกระดับมาตรฐาน AWS Identity & Access Governance สำหรับบัญชีที่ตกลง

**Scope:** ทบทวน Federation/Identity Center, IAM Role & Permission Set, MFA, SCP, Break-glass และ Access Review พร้อมปรับใช้ Priority Controls ที่อนุมัติ

**รายการที่จะดำเนินการ**

1. Review AWS Organization/Account และ Existing IAM  (1 วัน)
2. ออกแบบ IAM Standard, Federation, Roles และ Guardrails  (2 วัน)
3. Implement Priority Controls บน Accounts ที่ตกลง  (2 วัน)
4. Validate Access และส่งมอบ Governance Runbook  (1 วัน)

**Deliverables:** AWS IAM Baseline, Priority Finding List, Applied Control Evidence และ Governance Guide

**ระยะเวลา:** 6 Man-days

**ข้อจำกัด/เงื่อนไข:** การเปลี่ยน SCP/Role ต้องทดสอบผลกระทบและรับอนุมัติ; ไม่รวมการปรับสิทธิ์ทุก Account

### 06. Microsoft 365 Security Baseline & Secure Score Improvement

**รายละเอียดโดยย่อ:** ประเมิน Security Baseline ของ Microsoft 365 และปรับปรุง Controls ที่มีผลต่อความเสี่ยงและ Secure Score

**Scope:** ครอบคลุมการตั้งค่า Entra, Exchange Online, SharePoint/Teams และ Defender ตามสิทธิ์ใช้งานที่มี พร้อม Remediation ที่อนุมัติและ Exception Register

**รายการที่จะดำเนินการ**

1. Assess Tenant Configuration, Licensing และ Secure Score  (1 วัน)
2. จัดลำดับ Security Gaps และเลือก Priority Controls  (1 วัน)
3. Implement Remediation ที่ตกลง  (2 วัน)
4. Validate Configuration และจัดทำ Remaining Roadmap  (1 วัน)

**Deliverables:** Security Gap Assessment, Remediation Record, Secure Score Snapshot และ Exception Register

**ระยะเวลา:** 5 Man-days

**ข้อจำกัด/เงื่อนไข:** เป้าหมายการปรับปรุง Secure Score ขึ้นอยู่กับคะแนนเริ่มต้น สิทธิ์ใช้งาน และการอนุมัติเปลี่ยนแปลง ไม่รับประกันผลภายในระยะเวลาตัวอย่าง

### 07. Microsoft 365 Zero Trust – Regulatory & Compliance Readiness

**รายละเอียดโดยย่อ:** ประเมินความพร้อมด้าน Data Governance และ Compliance บน Microsoft 365/Purview

**Scope:** Review Information Protection, Retention, Audit, Records และ eDiscovery เทียบกับข้อกำหนดที่ลูกค้าระบุ พร้อมแก้ไข Controls ลำดับสำคัญเฉพาะขอบเขตที่อนุมัติ

**รายการที่จะดำเนินการ**

1. กำหนด Requirement และ Control Scope ร่วมกับทีม Compliance  (1 วัน)
2. Review Purview Capabilities และ Current Settings  (1.5 วัน)
3. จัดทำ Gap Analysis และ Prioritized Controls  (1 วัน)
4. Implement/Pilot Priority Controls ที่ตกลง  (1.5 วัน)
5. Validate และส่งมอบ Compliance Remediation Roadmap  (1 วัน)

**Deliverables:** Compliance Gap Matrix, Control Evidence, Pilot Configuration และ Remediation Roadmap

**ระยะเวลา:** 6 Man-days

**ข้อจำกัด/เงื่อนไข:** ไม่รวม Legal Opinion/การรับรองผ่านข้อกำหนดทางกฎหมาย; การใช้ Feature ขึ้นกับ License

### 08. Microsoft 365 Zero Trust – Secure AI Apps & Data

**รายละเอียดโดยย่อ:** ประเมินและจำกัดความเสี่ยงจาก AI Apps/Copilot และการเข้าถึงข้อมูลบน Microsoft 365

**Scope:** ทบทวน AI/Copilot Usage, Enterprise/OAuth Apps, Data Exposure, DLP, Sensitivity Labels และ Cloud App Controls โดย Pilot การบังคับใช้นโยบายที่เลือก

**รายการที่จะดำเนินการ**

1. Discover AI Apps, Copilot Use Cases และ Data Flows  (1 วัน)
2. Assess App Permissions และ Data Exposure Risks  (1.5 วัน)
3. ออกแบบ DLP/Label/App Control Priority Policies  (1 วัน)
4. Implement/Pilot Agreed Controls  (1.5 วัน)
5. Validate และจัดทำ Usage/Security Guidance  (1 วัน)

**Deliverables:** AI App/Data Risk Assessment, Policy Matrix, Pilot Control Evidence และ Action Plan

**ระยะเวลา:** 6 Man-days

**ข้อจำกัด/เงื่อนไข:** เน้น Assessment และ Selected Controls ไม่รวม Full Tenant Rollout; ฟีเจอร์ขึ้นกับ License

### 09. Enterprise MCP Server Implementation & Integration

**รายละเอียดโดยย่อ:** ออกแบบและพัฒนา MCP Server เพื่อให้ AI Clients เรียกใช้งาน Enterprise APIs/ข้อมูลที่ได้รับอนุญาต

**Scope:** สร้าง MCP Server, Tools, Authentication/Authorization, Secrets/Logging และ Deployment สำหรับ Use Case ที่ตกลง โดยใช้ Enterprise API หรือ Data Source ที่มีอยู่

**รายการที่จะดำเนินการ**

1. กำหนด Use Case, Tool Contract และ API/Data Source  (1 วัน)
2. ออกแบบ MCP Architecture และ Access Control  (1 วัน)
3. พัฒนา MCP Server และ Tools ตาม Scope  (2 วัน)
4. Deploy, ตั้งค่า Logging/Secrets และ Functional/Security Test  (1.5 วัน)
5. จัดทำ Runbook และ Knowledge Transfer  (0.5 วัน)

**Deliverables:** MCP Server & Selected Tools, Test Evidence, Configuration/Deployment Guide

**ระยะเวลา:** 6 Man-days

**ข้อจำกัด/เงื่อนไข:** ประมาณการ 6 วันสำหรับ 1 Data Source/API ที่พร้อมใช้ และไม่เกิน 3 Tools; ไม่รวมสร้าง Backend API ใหม่หรือ HA

### 10. Professional Support

**รายละเอียดโดยย่อ:** บริการให้คำปรึกษาและแก้ไขปัญหาระบบ Infrastructure, Identity, Microsoft 365 และ Cloud ตามที่ร้องขอ

**Scope:** Architecture/Design Review, Troubleshooting, Security Advisory, Configuration Review, Change Support, Health Check และ Knowledge Transfer ตาม Service Requests ที่ตกลง

**รายการที่จะดำเนินการ**

1. รับและจัดลำดับ Service Requests
2. วิเคราะห์ Incident/Problem และให้ Technical Recommendation
3. Review/Support การเปลี่ยนแปลง Configuration
4. บันทึก Effort, ผลดำเนินงาน และ Knowledge Transfer

**Deliverables:** Work Log/Time Sheet, Technical Findings และ Recommendation ตามงานที่ดำเนินการ

**ระยะเวลา:** 100 ชั่วโมง

**ข้อจำกัด/เงื่อนไข:** บริการตามการใช้จริงภายใน 100 ชั่วโมง (เทียบเท่า 12.5 Man-days); ไม่รวม 24×7 On-call หรือ Guaranteed SLA

## หมายเหตุ

- ระยะเวลาเป็น Professional Service Effort โดยประมาณ; Schedule จริงขึ้นกับข้อมูล, การอนุมัติ Change และความพร้อมของทีมที่เกี่ยวข้อง
- ขอบเขตการปรับใช้สำหรับรายการที่เป็น Pilot, Priority Controls หรือ Reference Implementation ไม่รวมการ Rollout ทั้งองค์กร เว้นแต่ตกลงเพิ่มเติม
- Windows Server 2016 Migration Implementation ต้องประเมินขอบเขตและจำนวน Server/Workloads เพิ่มเติมก่อนกำหนดระยะเวลา
- รายละเอียดขอบเขตและ Effort ต้องปรับตามขนาดสภาพแวดล้อมจริงก่อนจัดทำ SOW ฉบับสมบูรณ์