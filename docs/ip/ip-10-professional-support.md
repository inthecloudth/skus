# IP-10: Professional Support

> **Type:** Repeatable Service Package  
> **Delivery Unit:** 1 Support Block ขนาดตัวอย่าง 100 ชั่วโมง ปรับเพิ่มลดได้ตาม Engagement  
> **Baseline Effort:** 100 ชั่วโมง

## Objective

บริการให้คำปรึกษาและแก้ไขปัญหาระบบ Infrastructure, Identity, Microsoft 365 และ Cloud ตามที่ร้องขอ

## Scope

Architecture/Design Review, Troubleshooting, Security Advisory, Configuration Review, Change Support, Health Check และ Knowledge Transfer ตาม Service Requests ที่ตกลง

## Architecture Mental Model

**System question:** How does a reported symptom become a verified system outcome without bypassing ownership?

This is a conceptual system model, not a physical topology or deployment blueprint. Solid arrows represent interactions or changes; dashed arrows represent observation, constraints, or proposed relationships.

```mermaid
flowchart LR
  Reporter["Service requester"] -->|request + impact| Queue["Service request queue"]
  subgraph Support["Support operating boundary"]
    Triage["Triage + ownership"]
    Diagnose["Evidence-driven diagnosis"]
    Decision{"Action approval needed?"}
    Action["Approved change / workaround"]
    Verify["Requester validation"]
    Triage --> Diagnose --> Decision
    Decision -->|yes / approved| Action --> Verify
    Decision -->|no change| Verify
  end
  Queue --> Triage
  Systems["Infrastructure · identity · cloud systems"] -.->|logs / state / events| Diagnose
  Action -->|controlled intervention| Systems
  Verify -->|outcome + effort| Record["Resolution notes + work log"]
  Record -.->|recurrent issues| Triage
  classDef actor fill:#edf2f7,stroke:#64748b,color:#0f172a
  classDef control fill:#e0edff,stroke:#2563eb,color:#0f172a
  classDef result fill:#e7f5ed,stroke:#21805b,color:#0f172a
  class Reporter,Queue,Systems actor
  class Triage,Diagnose,Decision,Action,Verify control
  class Record result
```

## State & Control Model

```mermaid
stateDiagram-v2
  [*] --> Received
  Received --> Triaged: classify impact and owner
  Triaged --> Investigating: gather evidence
  Investigating --> ApprovedAction: remediation authorized
  Investigating --> Escalated: external dependency / out of scope
  ApprovedAction --> Verified: apply and test
  ApprovedAction --> Restored: change fails / revert
  Restored --> Investigating: continue diagnosis
  Verified --> Closed: requester confirms + log time
  Escalated --> Closed: owner accepts handoff
  Closed --> [*]
```

**Invariants**

- Safety — Any production change requires the relevant owner's approval and a proportionate verification or rollback plan.
- Accountability — Each request has an owner, an outcome, and recorded effort; a handoff is not the same as a technical resolution.
- Contract — Effort-based support does not automatically imply 24×7 coverage or an incident-response SLA.

**Failure / recovery reasoning:** No approved mitigation exists or required access is unavailable → escalate to the accountable owner, preserve the incident evidence, and record the handoff.

## Required Inputs / Prerequisites

Service Request Channel, Request Approver, Service Windows, Support Contacts, Work Log Template

## Standard Delivery Activities

1. รับและจัดลำดับ Service Requests
2. วิเคราะห์ Incident/Problem และให้ Technical Recommendation
3. Review/Support การเปลี่ยนแปลง Configuration
4. บันทึก Effort, ผลดำเนินงาน และ Knowledge Transfer

## Deliverables

Work Log/Time Sheet, Technical Findings และ Recommendation ตามงานที่ดำเนินการ

## Acceptance Criteria

มี Service Records, Time Sheet และ Findings/Recommendations สำหรับคำขอที่ดำเนินการในรอบ

## Reusable Delivery Assets

Service Request Register, Time Sheet, Technical Findings & Handover

## Assumptions & Exclusions

บริการตามการใช้จริงภายใน 100 ชั่วโมง (เทียบเท่า 12.5 Man-days); ไม่รวม 24×7 On-call หรือ Guaranteed SLA

## Reuse Guidance

ก่อนนำไปใช้ซ้ำ ให้ยืนยัน Delivery Unit, Scope Boundary, Dependencies, ผู้รับผิดชอบ Validation และปรับ Effort ตามขนาดงานจริง
