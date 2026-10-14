# IP-06: Microsoft 365 Security Baseline & Secure Score Improvement

> **Type:** Repeatable Service Package  
> **Delivery Unit:** 1 Microsoft 365 Tenant และชุด Priority Controls ที่ตกลง  
> **Baseline Effort:** 5 Man-days

## Objective

ประเมิน Security Baseline ของ Microsoft 365 และปรับปรุง Controls ที่มีผลต่อความเสี่ยงและ Secure Score

## Scope

ครอบคลุมการตั้งค่า Entra, Exchange Online, SharePoint/Teams และ Defender ตามสิทธิ์ใช้งานที่มี พร้อม Remediation ที่อนุมัติและ Exception Register

## Architecture Mental Model

**System question:** Where are user access decisions made, and how is configuration drift detected?

This is a conceptual system model, not a physical topology or deployment blueprint. Solid arrows represent interactions or changes; dashed arrows represent observation, constraints, or proposed relationships.

```mermaid
flowchart LR
  People["Workforce + external users"] --> Identity["Microsoft Entra ID"]
  subgraph Services["Microsoft 365 service boundary"]
    Identity -->|authenticated access| Workloads["Exchange · SharePoint · Teams"]
    Workloads -->|events| Telemetry["Audit + Defender signals"]
  end
  subgraph Improvement["Security governance loop"]
    Review["Secure Score + baseline assessment"]
    Prioritize["Risk-ranked controls"]
    Change["Approved configuration update"]
    Evidence["Before / after validation"]
    Review --> Prioritize --> Change --> Evidence
  end
  Identity -.->|review configuration| Review
  Workloads -.->|review configuration| Review
  Telemetry -.->|risk evidence| Review
  Change -.->|apply scoped change| Identity
  Change -.->|apply scoped change| Workloads
  Evidence -.->|track residual gaps| Review
  classDef live fill:#edf2f7,stroke:#64748b,color:#0f172a
  classDef control fill:#e0edff,stroke:#2563eb,color:#0f172a
  classDef result fill:#e7f5ed,stroke:#21805b,color:#0f172a
  class People,Identity,Workloads live
  class Review,Prioritize,Change control
  class Telemetry,Evidence result
```

## State & Control Model

```mermaid
stateDiagram-v2
  [*] --> Observed
  Observed --> Prioritized: measure baseline + risk
  Prioritized --> Approved: choose feasible controls
  Approved --> Applied: change configuration
  Applied --> Verified: test expected behavior
  Applied --> Reverted: unexpected user impact
  Reverted --> Prioritized: revise control
  Verified --> Monitored: capture evidence + exceptions
  Monitored --> Observed: new risk / baseline drift
  Monitored --> [*]
```

**Invariants**

- Safety — A score improvement is not proof that tenant risk is eliminated; prioritize independently using exposure and business impact.
- Change control — Do not deploy tenant-wide restrictions without an approved scope and validation path.
- Progress — Every selected control results in validated remediation, a tracked exception, or a documented blocker.

**Failure / recovery reasoning:** Conditional Access or workload control blocks legitimate business operations → revert the scoped change and use the evidence to refine policy.

## Required Inputs / Prerequisites

Tenant Configuration Access, License Inventory, Security Score Snapshot และผู้อนุมัติ Changes

## Standard Delivery Activities

1. Assess Tenant Configuration, Licensing และ Secure Score  (1 วัน)
2. จัดลำดับ Security Gaps และเลือก Priority Controls  (1 วัน)
3. Implement Remediation ที่ตกลง  (2 วัน)
4. Validate Configuration และจัดทำ Remaining Roadmap  (1 วัน)

## Deliverables

Security Gap Assessment, Remediation Record, Secure Score Snapshot และ Exception Register

## Acceptance Criteria

มีรายการ Security Gaps, Evidence ของการปรับค่าและผลตรวจสอบ, Exception Register และ Next-step Roadmap

## Reusable Delivery Assets

Security Baseline Checklist, Findings Register, Validation Record

## Assumptions & Exclusions

เป้าหมายการปรับปรุง Secure Score ขึ้นอยู่กับคะแนนเริ่มต้น สิทธิ์ใช้งาน และการอนุมัติเปลี่ยนแปลง ไม่รับประกันผลภายในระยะเวลาตัวอย่าง

## Reuse Guidance

ก่อนนำไปใช้ซ้ำ ให้ระบุจำนวนระบบและ Policy ที่ครอบคลุม กำหนดผู้อนุมัติการเปลี่ยนแปลง และปรับ Effort ตามความซับซ้อนจริง
