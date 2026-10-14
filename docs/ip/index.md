# Reusable Service IP Packages

คลัง **Repeatable Professional Services Packages** สำหรับ Infrastructure, Cloud, Identity, Security และ AI Integration

แต่ละ IP เป็นขอบเขตงานอิสระ มี Objective, Scope, Prerequisites, Standard Delivery Activities, Deliverables, Acceptance Criteria, Assumptions และ Effort เบื้องต้น

**หมายเหตุ:** Effort แสดง Man-days/ชั่วโมงตัวอย่าง ใช้สำหรับการวางแผน ไม่ใช่ระยะเวลาตามปฏิทิน

| IP | Service Package | Baseline Effort |
|---|---|---|
| 01 | [Windows Server 2016 Migration Assessment & Roadmap](ip-01-windows-server-migration-assessment.md) | 6 Man-days |
| 02 | [Windows Server 2016 Migration Implementation](ip-02-windows-server-migration-implementation.md) | TBD ตามขอบเขต |
| 03 | [Service Account Security Assessment & Remediation](ip-03-service-account-security.md) | 6 Man-days |
| 04 | [Linux Platform Management, Standardization & Security](ip-04-linux-standardization-hardening.md) | 7.5 Man-days |
| 05 | [AWS Identity & Access Governance and Security Baseline](ip-05-aws-identity-access-baseline.md) | 6 Man-days |
| 06 | [Microsoft 365 Security Baseline & Secure Score Improvement](ip-06-m365-security-baseline.md) | 5 Man-days |
| 07 | [Microsoft 365 Zero Trust – Regulatory & Compliance Readiness](ip-07-m365-compliance-readiness.md) | 6 Man-days |
| 08 | [Microsoft 365 Zero Trust – Secure AI Apps & Data](ip-08-secure-ai-apps-data.md) | 6 Man-days |
| 09 | [Enterprise MCP Server Implementation & Integration](ip-09-enterprise-mcp-server.md) | 6 Man-days |
| 10 | [Professional Support](ip-10-professional-support.md) | 100 ชั่วโมง |

## Architecture Mental Models

แต่ละ IP ประกอบด้วยแผนภาพ **2 มุมมอง** เพื่อให้ผู้อ่านเข้าใจระบบโดยไม่ต้องเริ่มจากชื่อผลิตภัณฑ์หรือขั้นตอนติดตั้ง:

1. **Architecture Mental Model (Structure):** ขอบเขตของระบบ (boundary), actors, state holders, interactions, trust boundaries และ control points; ลูกศรทึบคือ interaction/change และลูกศรประคือ observation/constraint/proposed relationship
2. **State & Control Model (Behavior):** สถานะที่ระบบหรือกิจกรรมผ่านไปได้, เงื่อนไข transition, กรณี failure/recovery และข้อกำหนดที่ต้องเป็นจริงตลอด (**invariants**)

ส่วน **Safety** ช่วยตอบว่าอะไร *ห้ามเกิดขึ้น* และ **Progress** ช่วยตอบว่าการดำเนินงานจะไปสู่ผลลัพธ์ใดภายใต้เงื่อนไขที่ตกลง ก่อนปรับใช้กับระบบจริงต้องยืนยัน assumptions กับเจ้าของระบบ

> Diagram-as-code ทุกภาพเขียนด้วย Mermaid และแก้ไขได้ใน Markdown โดยตรง ภาพเป็น conceptual models สำหรับใช้ reasoning ไม่ใช่ผัง Physical Deployment และไม่ใช่แผนผังระบบของลูกค้าจริง

### Design approach

แนวทางการลดระบบให้เหลือองค์ประกอบ, state transitions และ invariants ได้แรงบันดาลใจจากบทความสาธารณะของ Dominik Tornow ได้แก่

- [Imperative vs Declarative — State Machine Model](https://dominik-tornow.medium.com/imperative-vs-declarative-8abc7dcae82e)
- [A Tale of Two Dimensions — Minimal, Self-consistent Mental Models](https://dominik-tornow.medium.com/a-tale-of-two-spectrums-df6035f4f0e1)
- [Handling Failures From First Principles — Detection and Mitigation](https://dominik-tornow.medium.com/handling-failures-from-first-principles-1ed976b1b869)

แผนภาพในคลังเป็นงานจัดทำขึ้นใหม่เพื่ออธิบาย Service IP แต่ละรายการ ไม่ใช่การนำแผนภาพต้นฉบับมาใช้หรือผลงานที่ผู้เขียนบทความรับรอง
## การนำ IP ไปใช้ซ้ำ

1. เลือก IP ที่ตรงกับความต้องการ และกำหนด **Delivery Unit / Target Systems** ของ Engagement
2. ตรวจ **Required Inputs / Prerequisites** ว่ามีครบ
3. ปรับ **Scope, Effort, Dependencies และ Exclusions** ตามจำนวนระบบและ Complexity จริง
4. ใช้กิจกรรมและ **Acceptance Criteria** เพื่อกำหนด Deliverables และเกณฑ์รับมอบ
5. จัดทำ SOW ราย Engagement แยกจาก IP กลาง และไม่บันทึกข้อมูลที่ระบุองค์กรเฉพาะในคลังนี้

---
คลังนี้เป็นเอกสารแม่แบบทางเทคนิค ไม่ใช่เอกสาร Statement of Work ฉบับลงนาม
