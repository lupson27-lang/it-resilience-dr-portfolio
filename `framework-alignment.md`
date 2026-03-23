# ISO 27001 and NIST CSF Alignment

## How I Map Operational Resilience to Frameworks

I use both frameworks in complementary ways. ISO 27001 provides the **governance structure** (Annex A controls, certification requirements). NIST CSF provides the **functional lens** (Identify, Protect, Detect, Respond, Recover).

## Framework Integration

```mermaid
graph LR
    subgraph ISO27001
        A12[Operations Security]
        A17[Business Continuity]
        A18[Compliance]
    end
    
    subgraph NIST_CSF
        RS[Respond]
        RC[Recover]
        PR[Protect]
    end
    
    A12 --> PR
    A17 --> RC
    A17 --> RS
```

## Key Controls I Focus On

| ISO 27001 Control | NIST CSF Function | My Application |
| :--- | :--- | :--- |
| A.12.1 – Operational Procedures | Protect | Runbooks, change management, documented recovery steps |
| A.12.3 – Backup | Recover | Backup verification, restore testing, offsite/immutable copies |
| A.12.6 – Technical Vulnerability Management | Protect | Patching, configuration hardening |
| A.16.1 – Incident Management | Respond | Escalation workflows, incident coordination, root cause analysis |
| A.17.1 – Business Continuity | Respond / Recover | DR tests, BC exercises, post-incident improvement |
| A.17.2 – Redundancies | Recover | High availability, failover configurations, geographic redundancy |

## Framework Alignment Map

```mermaid
graph TB
    subgraph NIST[NIST Cybersecurity Framework]
        ID[Identify]
        PR[Protect]
        DE[Detect]
        RS[Respond]
        RC[Recover]
    end
    
    subgraph ISO[ISO 27001 Annex A]
        A5[Policy]
        A6[Organization]
        A8[Asset Management]
        A12[Operations Security]
        A16[Incident Management]
        A17[Business Continuity]
        A18[Compliance]
    end
    
    subgraph MY[My Resilience Focus]
        BCP[Business Continuity Planning]
        DR[Disaster Recovery Testing]
        BACKUP[Backup & Restore]
        INCIDENT[Incident Response]
    end
    
    A17 --> RC
    A12 --> PR
    A16 --> RS
    A8 --> ID
    
    RC --> BCP
    RC --> DR
    PR --> BACKUP
    RS --> INCIDENT
    
    BCP --> RC
    DR --> RC
    BACKUP --> PR
    INCIDENT --> RS
    
    style MY fill:#d3f9d8
    style RC fill:#ffd43b
    style PR fill:#ffd43b
    style RS fill:#ffd43b
```

## My Framework Mindset

Frameworks are not checklists. I use them to:

- **Ensure coverage** – No critical resilience domain is overlooked
- **Provide audit-ready documentation** – Clear traceability between controls and implemented measures
- **Communicate risk posture** – Translate technical resilience into language leadership understands
- **Drive continuous improvement** – Structured review cycles based on framework requirements
