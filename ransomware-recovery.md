| :--- | :--- |
| `ransomware-recovery.md` | (Provided after this table) |
| `sample-dr-runbook.md` | (Provided after this table) |
| `framework-alignment.md` | (Provided after this table) |

---

#### `ransomware-recovery.md`

```markdown
# Ransomware Recovery Considerations

## The Reality

Ransomware attacks have changed what "resilience" means. If an attacker compromises admin credentials, they can often delete or encrypt backups stored in the same environment.

## My Approach to Ransomware-Resilient Recovery

### 1. Isolation
- Immutable backups that cannot be modified or deleted for a defined retention period
- Air-gap or logical separation between production and backup environments
- Separate admin credentials for backup infrastructure

### 2. Recovery Validity
- Regular restore testing—not just backup success checks
- Test restores to isolated environments to validate data integrity before production recovery
- Document restore times to inform realistic RTOs

### 3. Recovery Planning
- Prioritized restoration order based on business impact
- Clean room / known good infrastructure for restoration
- Communication plan that accounts for potential extended downtime

## Key Questions I Ask When Assessing Ransomware Resilience

- Can the attacker who compromises production also delete backups?
- When was the last successful *restore* test?
- What is the worst-case recovery time if primary infrastructure is encrypted?
- Are offline or immutable copies available?

## Ransomware-Resilient Backup Architecture

```mermaid
flowchart LR
    subgraph PROD[Production Environment]
        APP[Application Servers]
        DB[(Databases)]
        FILE[File Servers]
    end
    
    subgraph BACKUP[Backup Environment]
        PRI[Primary Backup Storage]
        IMM[Immutable Backup]
        OFFSITE[Offsite / Air-Gap]
    end
    
    subgraph ATTACK[Ransomware Attack]
        COMP[Attacker Compromises Prod]
        ENCRYPT[Data Encrypted]
    end
    
    APP --> PRI
    DB --> PRI
    FILE --> PRI
    PRI -->|Immutable Copy| IMM
    PRI -->|Offsite Replication| OFFSITE
    
    COMP --> ENCRYPT
    ENCRYPT -.-x PRI
    
    IMM -->|Clean Recovery| RECOVER[Recovery Environment]
    OFFSITE -->|Clean Recovery| RECOVER
    
    style COMP fill:#ff6b6b
    style ENCRYPT fill:#ff6b6b
    style IMM fill:#51cf66
    style OFFSITE fill:#51cf66
    style RECOVER fill:#51cf66
