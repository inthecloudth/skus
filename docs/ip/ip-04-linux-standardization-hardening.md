# IP-04: Linux Platform Management, Standardization & Security

> **Type:** Repeatable Service Package  
> **Delivery Unit:** One reference configuration for an agreed Linux distribution and version  
> **Baseline Effort:** 7.5 Man-days

## Objective
กำหนดแนวทางบริหารจัดการ Linux ให้เป็นมาตรฐาน พร้อมสร้าง Reference Configuration ที่สามารถนำไปใช้ซ้ำได้

## Scope
ทบทวนสภาพแวดล้อม Linux และจัดทำมาตรฐานการตั้งค่า การดูแลระบบ การติดตามสถานะ และการสำรองข้อมูลสำหรับกลุ่มระบบที่ตกลง

## Architecture Mental Model

**System question:** How do many Linux hosts converge on one declared operating baseline?

This is a conceptual system model, not a physical topology or a deployment blueprint. Solid arrows show an intended interaction or change; dashed arrows represent observation, constraints, or a proposed relationship.

```mermaid
flowchart LR
  Operator["Platform operator"] --> Standard["Approved Linux standard"]
  subgraph Control["Configuration control"]
    Standard --> Desired["Desired baseline"]
    Compare["Drift comparison"]
    Action["Approved configuration change"]
    Desired --> Compare --> Action
  end
  subgraph Host["Reference Linux host"]
    Access["Identity · SSH · sudo"]
    System["Packages · services · patch level"]
    Observe["Logs · monitoring · backup status"]
    Access --> System --> Observe
  end
  System -.->|actual state| Compare
  Action -->|apply| System
  Observe -.->|verify| Compare
  classDef live fill:#edf2f7,stroke:#64748b,color:#0f172a
  classDef policy fill:#e0edff,stroke:#2563eb,color:#0f172a
  classDef signal fill:#e7f5ed,stroke:#21805b,color:#0f172a
  class Operator,Access,System live
  class Standard,Desired,Compare,Action policy
  class Observe signal
```

## State & Control Model

```mermaid
stateDiagram-v2
  [*] --> Unknown
  Unknown --> Measured: collect current configuration
  Measured --> Drift: differs from baseline
  Measured --> Compliant: matches baseline
  Drift --> Approved: scope + impact reviewed
  Approved --> Applied: reference configuration
  Applied --> Compliant: validate controls
  Applied --> Drift: tests fail / restore
  Compliant --> Drift: future configuration drift
  Compliant --> [*]
```

**Invariants**

- Safety — Security and access changes must preserve an approved operational access path.
- Convergence — Drift is measured against the same versioned baseline, not against another arbitrary server.
- Scope — Reference validation does not imply fleet-wide deployment.

**Failure / recovery reasoning:** A baseline change breaks application access or management → revert the affected change, capture exception, and revise the baseline.

## Required Inputs / Prerequisites
รายการระบบและ Distribution/Version เป้าหมาย, นโยบายองค์กร, ทีมเจ้าของระบบ และข้อมูลเครื่องมือบริหารจัดการที่ใช้อยู่

## Standard Delivery Activities
1. สำรวจสภาพแวดล้อม Linux และ Current Configuration (1 วัน)
2. จัดทำ Standard Build และ Configuration Baseline (2 วัน)
3. จัดทำ Reference Configuration และเชื่อมต่อระบบบริหารจัดการที่มีอยู่ (2.5 วัน)
4. ตรวจสอบผล จัดทำ Operations Guideline และ Knowledge Transfer (2 วัน)

## Deliverables
Linux Standard Baseline, Reference Configuration, Validation Checklist และ Operations Guideline

## Acceptance Criteria
Reference Configuration ผ่านการทดสอบตาม Checklist ที่ตกลง และส่งมอบเอกสารสำหรับการนำไปใช้งานซ้ำ

## Reusable Delivery Assets
Linux Baseline Checklist, Build Standard, Configuration Record และ Validation Checklist

## Assumptions & Exclusions
ขอบเขตเป็นการสร้างมาตรฐานและ Reference Implementation; ไม่รวมการ Rollout ไปยัง Linux ทุกเครื่องในองค์กร

## Reuse Guidance
ระบุระบบเป้าหมาย Distribution/Version และข้อกำหนดให้ชัดเจนก่อนนำแพ็กเกจไปใช้ซ้ำ และปรับ Effort เมื่อมีหลาย Platform หรือความซับซ้อนเพิ่มขึ้น
